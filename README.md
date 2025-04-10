# Crystallography by D. M. Esteves (INESC MN/IST-ULisboa)
This is a Mathematica script to perform algebraic calculations of distances and angles between planes and directions in crystallography.

Requirements:
Mathematica >= 13.3

Quick guide:
1. To get started, you should create a list of rules ("params") with your lattice parameters. You can use your favourite units for lengths, as the results will be given in the same units. For angles, please use degrees. Example: for NaCl, a->0.56402 nm.

2. For X-ray diffraction calculations, you should also suppy a rule ("diffrac") for the wavelength of your favourite radiation. Make sure you are consistent with the "params" units! Example: for the Cu Kα1, λ->0.15406 nm.

3. Then, you should fill in the metric tensor according to the system you are dealing with (e.g., for NaCl, the metric tensor is a I, where I is the 3x3 identity matrix). You should also fill in the "assump" rule to assert the positivity of the lengths and the quadrants of the angles. Example: NaCl, a>0.

4. Evaluate all the initialisation cells.

5. Calculate! The available functions include:
	- DirectLength[u,v,w]: gives the length of the vector with fractional coordinates [u v w], in direct space.
	- ReciprocalLength[h,k,l]: gives the length of the vector with Miller indices (h k l), in reciprocal space.
	- DistancePlanes[h,k,l]: gives the interplanar distance of the planes with Miller indices (h k l).
	- AngleDirections[u1,v1,w1,u2,v2,w2]: gives the angle (in degrees) between the directions with coordinates [u1 v1 w1] and [u2 v2 w2].
	- AnglePlanes[h1,k1,l1,h2,k2,l2]: gives the angle (in degrees) between the planes with Miller indices (h1 k1 l1) and (h2 k2 l2).
	- AnglePlaneDirection[h,k,l,u,v,w]: gives the angle (in degrees) between the normal to the plane with Miller indices (h k l) and the direction with coordinates [u v w].
	- ToDirectSpace[h,k,l]: gives the direction, in direct space, that corresponds to the normal of the plane with Miller indices (h k l). Note that it may not be possible to write the coordinates as integers. This is useful to determine channelling directions.
	- ToReciprocalSpace[u,v,w]: gives the plane, in reciprocal space, that corresponds to the the direction [u v w]. Note that it may not be possible to write the Miller indices as integers. 
	- Plane[u1,v1,w1,u2,v2,w2]: finds the Miller indices of the plane containing the axes [u1 v1 w1] and [u2 v2 w2].
	- MutuallyOrthogonal[h1,k1,l1,h2,k2,l2]: finds the Miller indices of the plane that is simultaneously orthogonal to the planes (h1 k1 l1) and (h2 k2 l2). The output may then be rationalised.
	- Q[h,k,l]: gives the length (in reciprocal space) of the reciprocal space vector associated with the planes with Miller indices (h k l).
	- Qz[h,k,l,m,n,o]: gives the component of the Q-vector associated with the plane with Miller indices (h k l) in the direction of the normal to the plane with Miller indices (m n o). Usually, (m n o) will be the surface plane, so Qz represents the perpendicular component of the scattering vector.
	- Qx[h,k,l,m,n,o]: gives the component of the Q-vector associated with the plane with Miller indices (h k l) in the direction along the plane with Miller indices (m n o). Usually, (m n o) will be the surface plane, so Qx represents the parallel component of the scattering vector.
	- 2θ[h,k,l,λ]: gives the 2θ angle associated with the plane with Miller indices (h k l), for a radiation with wavelength λ.
	- ωminus[h,k,l,m,n,o,λ]: gives the incidence angle associated with the plane with Miller indices (h k l), for a sample with surface (m n o), for a radiation with wavelength λ, in a grazing incidence geometry.
	- ωplus[h,k,l,m,n,o,λ]: gives the incidence angle associated with the plane with Miller indices (h k l), for a sample with surface (m n o), for a radiation with wavelength λ, in a grazing exit geometry.
	- ΔφXYZ[a,b,c,d,e,f,g,h,i]: gives the angle between the X=[P]ole/[D]irection (a b c)/[a b c] and the Y=[P]ole/[D]irection (d e f)/[d e f] in a sterographic projection where (g h i)/[g h i] is the Z=[P]ole/[D]irection corresponding to the surface. XYZ can be PPP, PPD, PDP, DDP, DDD, depending on the situation. E.g., ΔφPDP[1,2,3,4,5,6,7,8,9] would give the azimuthal angle between pole (1 2 3) and direction [4 5 6], for (7 8 9)-oriented sample.
