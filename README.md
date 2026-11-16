# Windows Server Active Directory Home Lab

**Status: Completed — core objectives verified**  
**Platform:** Oracle VirtualBox · **Domain:** `homelab.test` · **Client:** `WIN11-CLIENT`

A practical two-VM Windows infrastructure project demonstrating Active Directory deployment, centralized user management, domain authentication, and a tested Group Policy restriction. The walkthrough includes curated screenshots, including troubleshooting rather than only successful end states.

## Lab topology

```text
Oracle VirtualBox (Windows host)
├── Windows Server (DC01) — AD DS / DNS / homelab.test
└── Windows 11 Pro (WIN11-CLIENT)
    └── Domain user HOMELAB\jsmith; custom user GPO applied
```

## Step-by-step walkthrough

1. [VirtualBox and Windows Server setup](walkthrough/01-01-virtualbox-server.md)
2. [Server network preparation](walkthrough/02-02-networking.md)
3. [Active Directory deployment and domain creation](walkthrough/03-03-active-directory.md)
4. [Organizational units, users and groups](walkthrough/04-04-users-groups.md)
5. [Windows 11 client setup and storage troubleshooting](walkthrough/05-05-windows11.md)
6. [Domain join and domain-user sign-in](walkthrough/06-domain-join-and-login.md)
7. [Group Policy configuration, troubleshooting and verification](walkthrough/07-group-policy.md)

## Verified outcomes

- Installed Active Directory Domain Services and promoted Windows Server to a domain controller for `homelab.test`.
- Created the `Lab-Users` organizational unit, test user `John Smith` (`jsmith`), and `IT-Support` global security group; verified membership.
- Installed Windows 11 Pro in VirtualBox and resolved a host disk-space error by relocating the client VM to the V: SSD.
- Joined `WIN11-CLIENT` to the domain and signed in using `HOMELAB\jsmith`.
- Created and linked **TEST GPO** to `homelab.test` and enabled **Prohibit access to Control Panel and PC settings**.
- Investigated an initial failed application (`gpresult` showed no applied user GPO), corrected GPO permissions, refreshed policy and confirmed **TEST GPO** was applied.
- Verified that opening Control Panel produced the Windows **Restrictions** error.

## Troubleshooting highlight

The custom policy initially did not apply even though `gpupdate /force` reported successful updates. We checked the user context and GPO permissions, adjusted security permissions, and reran the policy verification. `gpresult` then listed **TEST GPO** and the Control Panel restriction was enforced. This illustrates the difference between a successful policy refresh and a policy actually being applied to the intended user.

## Skills demonstrated

Windows Server · AD DS · DNS · Organizational Units · User and Group Management · Windows 11 · VirtualBox · Domain Join · Group Policy Management · Security Filtering · `whoami` · `gpupdate` · `gpresult` · Troubleshooting

## Evidence and publication note

Screenshots are selected to show key milestones and troubleshooting. Some installation and network configuration images show intermediate settings, not independent tests of every service. Before making the repository public, inspect screenshots for personal details, credentials, recovery information, and license keys. Do not upload VM disks or installation ISOs.
