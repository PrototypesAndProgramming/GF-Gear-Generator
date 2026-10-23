# GF-Gear-Generator
Main repo of the GF Gear Generator for Autodesk's Fusion 360.

Dear reader,

I am excited to share one of my earliest programming projects with you. When I embarked on this journey of learning programming, I poured my time and dedication into this project, which holds a special place in my heart. While the code quality may not be the best, the effort and genuine care invested in it are undeniable.

As of 17/05/2023, I have made the decision to release this project as an open-source endeavor. My aim is to invite the community to contribute and enhance it further, making it a collaborative effort that benefits everyone.

I truly believe that by opening up this project, we can collectively improve and refine it.

Thank you for joining me on this journey, and I look forward to witnessing the growth and evolution of this project together.

*********************************************** 29/06/2023 Updates ************************************************

The GFGG is about to undergo some great code quality improvements as it will follow the OOP structure I'm using for STLGears.com . To understand what will be changed I've added the UML diagram bellow so you can get an idea of the stuff that's to come:

![UML Diagram](./UML_Diagram.png)
*********************************************** Root clearance / backlash fix ************************************************

This fork fixes gears whose tooth tips touched (and in practice intersected) the root cylinder of the mating gear:

- Spur, helical, internal (ring) and planetary gears now get the standard bottom clearance of 0.25 × module
  (dedendum 1.25 m, addendum 1.0 m). Previously addendum and dedendum were both 1.0 m, so the tip of one gear sat
  exactly on the root circle of its mate. Backlash is a tangential allowance and never changed this radial gap.
- The Backlash input on the standard spur gear was never read; it is now applied. It is also now passed through on
  the non-standard spur/helical paths with zero profile shift and is honoured by profile-shifted tooth profiles.
- Helical twist is now computed from the true pitch radius instead of being inferred from tooth depth, which was
  off by ~1% for typical gears and made meshing helical gears slightly mismatched.
