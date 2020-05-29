---
layout: default
permalink: /research/master-thesis/
---
# Master thesis proposal

## Soft manipulation
The ability to manipulate soft deformable objects of any scale is a prerequisite for advanced robot autonomy. The application of soft manipulation ranging from grasping and handling of everyday objects (food, clothing, etc.) in consumer robotics, surgical robotic procedures (manipulating tissues, guiding flexible needles, etc), picking up of agricultural products, or movement of large flexible objects (such as cables, ropes, and tents).

However, taking into account deformation introduces new challenges, in particular:
- The complication of **sensing deformation**
- The curse of **infinite dimensionality** of the deformation configuration
- The complexity of **high nonlinearity** in modeling the deformation

In the master thesis, we hope to address one of these challenges, depending on the interests of the student, I have two proposals available, students are welcomed to propose new ideas to solve these challenges.

### Hierarchical manipulation
In my previous work [Vision-based Manipulation of Deformable and Rigid Objects Using Subspace Projections of 2D Contours](https://hal.archives-ouvertes.fr/hal-02558064/file/main.pdf), I proposed a unified manipulation scheme for both rigid and deformable objects. The work is done by computing a local interaction model for manipulation. This approach enables manipulation with very short learning phase. However, the setback is that the framework computes only a local model therefore we can not guarantee global convergence.

In the hierarchical manipulation scheme we hope to overcome this setback with a (D)NN at higher level that simultaneously learns a global model while the local model enables fast manipulation.
### Generalized contact for soft manipulation
In my previous work [Robotic Manipulation Planning for Shaping Deformable Linear Objects With Environmental Contacts](https://hal.archives-ouvertes.fr/hal-02303257/document), I worked on contact for constraining the deformation. However, the contact analysis only works for a specific situation. In this master thesis, we hope to find a general approach for representing contact in the environment such that the robots are able to use them for constraining deformation in different scenarios.


## Expected outcomes
Since my [Workshop](https://jihong-zhu.github.io/research/IROS_workshop) was accepted at IROS 2020 in Las Vegas, an expected outcome of the master thesis could be a poster at the workshop. In addition, together with my co-organizers, we probably will submit a Special Issue at a robotics journal, so there is also possibility to submit the final thesis work to the journal.

## Possible collaborators outside TU Delft
The work could potentially be carried out collaboratively with:
- [Dr. David Navarro-Alacron](https://www.polyu.edu.hk/me/david/), [The Hong Kong Polytechnic University](https://www.polyu.edu.hk/web/en/home/index.html)
- [Dr. Andrea Cherubini](http://www.lirmm.fr/lirmm_eng/users/utilisateurs-lirmm/andrea-cherubini), [LIRMM IDH](http://www.lirmm.fr/lirmm_eng/research/equipes/idh)   

## Preferred background and skills
**Courses**
- Linear algebra
- Control systems
- Basic machine learning
- A knowledge on vision-based robot control (not necessary but desirable)

**Programming languages**

- Matlab/Python/C++
