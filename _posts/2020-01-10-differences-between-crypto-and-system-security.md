---
layout: post
title:  "Some thinkings of differences between cryptography and system security"
date:   2020-01-10 14:59:21 +0800
tags: blogs
color: rgb(255,90,90)
cover: '../assets/test.png'
subtitle: 'Differences between cryptography and system security'
---
It seems like  there is a understanding gap among security researchers from cryptography and system security.
Well, from my perspective, i would like to make a metaphor to describe `my` understanding towards it.

Before that, i need to point out, what i mean system security area is that all related security areas except cryptography researchers are focused on.

Let's say there is a building, whose foundation is the cryptography, but there are a lot of other systems like elevator or electric system are system security areas. The foundation also consists of various aspects, e.g. the physical basement of this building, power infrastructure for the electric system in this building and so on.

One day, if foundation is compromised by attacker, the building would never exist no matter how secure and perfect its electric system is. Worthy to mention, there is also many ways to compromise cryptography(foundation), like cryptanalysis (take differential analysis as an example) and quantum attack (which can just make traditional cryptography unsecure by super computional power)

But in the daily life, even foundation is secure, the implementation, deployment, protocol etc of various systems in this building could still have many vulnerabilities, which would make the system operation vulnerable to attacker. For instance, if the program of elevator is compromised, although the building doesn't fall down, but attacker could make the lift stopped at a certain floor to prevent anyone in this building to use it.

These are my thoughts about cryptography and other security areas. They both are vital and necessary research areas for security, just with different ways&angles.
