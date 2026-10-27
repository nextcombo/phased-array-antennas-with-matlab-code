# Phased Array Antennas [with MATLAB Code]

In this article, a concept and mathematical explanation of an array radar will be presented (with illustrations and animations). The importance of this antenna topology in recent applications, such as SpaceX's Starlink low-latency internet satellites, will be discussed in detail. Other fields where phased array antennas play a significant role, such as 5G technology, will be emphasized. To conclude the discussion, these devices encounter technical and potential health limitations will be addressed.
Figure 0. A directional pattern of a 3 × 3 circular microstrip phased array antenna
Introduction - Dipole Antenna
As emphasized in the name, a phased array antenna is constructed by arranging multiple individual antennas to form an array. Figure 1 shows a linear array antenna composed of dipole antennas.
Figure 1. Dipole linear phased array antenna
Before exploring the properties and operation of phased array antennas, reviewing the characteristics and simple yet very common operation of antennas is beneficial: dipole antennas. This will provide background and highlight the tremendous advantages of phased array antennas over any other antenna topology.
Before exploring the properties and operation of phased array antennas, reviewing the characteristics and simple yet very common operation of antennas is beneficial: dipole antennas. This will provide background and highlight the tremendous advantages of phased array antennas over any other antenna topology.
To put it briefly, the concept is quite simple. The specific implementation of transduction may be more difficult. To intuitively understand this phenomenon, let us look at a familiar circuit component: parallel plate capacitors.
Figure 2. Antenna acting as a wave converter.
As shown in Figure 3(a), when the capacitor is excited by a clockwise current, the charge and electric field distribution are as shown in the figure.
If we make a slight modification to this arrangement by connecting the wires to the edges of the capacitor and folding them as shown in Figure 3 (b), we can predict the distribution of the electric field, where the line follows the path from positive charge to negative charge. The distribution of charge may be more difficult to predict. Applying the free electron model, however, we can explain how free electrons in the conductor (wires and plate) are pushed and drift towards the end of the plate at the instant the capacitor is powered up. Henze expects that the edge of the plate will have more charge, while the charge distribution at the dipole center will be lower.
(a) Parallel Plate Capacitor (b) Dipole Antenna Current and Electric Field Direction
Figure 3. Transforming a parallel plate capacitor into a dipole antenna.
It's important to note that the current direction in both plates is the same. As we will see later, this is crucial because both currents contribute to generating a stronger H-field rather than cancelling each other out. There is an instant when the polarization of the current flips at the source, with the charge not yet fully drifted to the other side and maintaining a similar distribution but with the current flowing in the opposite direction, as shown in Figure 4.
Figure 4. AC and Charge Allocation.
For the operation frequency range of a dipole antenna, the voltage (or charge) distribution and current distribution can have or can not have an opposite orientation relative to each other. In any case, the current drives the charge drift, which responds with a certain delay. As we will see in discussions in Figure 5, this will generate propagating electromagnetic waves.
Applying the right-hand rule, as shown in Figure 5 (a), we obtain an H-field coming out from the right plane of the dipole. Since the electric field lines are nearly straight around the center of the dipole, we can approximate these two field lines around the center of the dipole to produce the electromagnetic wave shown in Figure 5 (b).
(a) Electric Field and Magnetic Field Lines (b) Forward-Propagating TEM Electromagnetic Wave
Figure 5. Dipole Antenna Produces Transverse Electromagnetic Waves
Power Transmission - Radiation Diagram
Currently, ongoing research models can more accurately describe the charge and current distribution of dipole antennas as well as many other antennas. For the purpose of this article and industry standards, the existing theories describing the properties of a dipole are consistent with the explanation provided above and can be found on the Dipole Wikipedia page. The animation of a half-wave dipole is borrowed because its length is half a wavelength, so we start studying its output radiation pattern.
As shown in Figure 6 (a). Voltage and current distribution are exactly opposite. When the current is maximum, the voltage is zero, and vice versa. Polarity is always opposite; when the current is positive, the voltage is negative, and vice versa. This is important because, when evaluating power propagation within a medium, we use the time-averaged Poynting vector given in equation 1.
Assuming time-harmonic fields, for calculating propagation power, we cross multiply the SAV of the phase-velocity electric field with the conjugate of the phase-velocity magnetic field. From the E H animation, we can predict that power propagation is higher at the center of the dipole compared to the edges. Using MATLAB's App: Antenna Designer, we obtain Figures (b) and (c), which provide an accurate description of the radiation pattern of a half-wave antenna at 60 MHz.
(a) Animation (b) Radiation pattern along the yz cross section (c) 3D radiation pattern of the 6.60 MHz half-wave dipole antenna
The same analysis can be conducted on different antenna topologies: for example, a helical antenna (Figure 7) or a tweeter antenna (Figure 8). As shown in these diagrams, the radiation patterns vary in shape and intensity. If an RF engineer team is tasked with selecting an antenna for a specific application, they must evaluate the required radiation pattern. For instance, a half-wave dipole will work well for AM radio if a radiated pattern of all-directionality is needed. Conversely, if more directionality is desired, such as in weather tracking or satellite TV, a helical or tweeter antenna might be more suitable. Despite the differences in their radiation patterns, these antennas share a common function: their radiation patterns are fixed. RF engineers or antenna designers find it nearly impossible to modify the shape of the radiation pattern without affecting other performance parameters. It is precisely due to the limitations of the universality of radiation modes that phased array antennas offer a distinct advantage: they allow for some degree of control over the radiation pattern and can be controlled on demand. We will see how this works in the next section.
Figure 7. Radiation pattern of a helical antenna.
Figure 8. Radiation pattern of a tweeter antenna.
Phased Array Antennas
To understand why and how these antennas have completely transformed the field of communication, we will start by analyzing what interference phenomena are (Figure 9). Remember, when a isotropic wave source produces a radiating wave and these waves hit walls with narrow openings or slits, the waves themselves become sources. The waves from two slits interact and produce an intensity pattern at certain distances on the screen.
Figure 9. The double-slit experiment illustrates the phenomenon of interference.
Because the propagation length of one wave differs from another at different points on the screen, there is a relative phase difference between the two waves. The two waves converge at different points on the screen, creating a sinc function intensity pattern based on the relative phase, as shown in Figure 9. By utilizing this concept, any number of physical antennas can replace the slits on the wall and utilize the interference phenomenon. The goal here is to control certain parameters of the transmitted antenna signal and obtain the desired radiation pattern.
Turning to
In circuits, two parameters that can control the signal are amplitude and phase (Figure 10(a)). Amplifiers, power dividers, or attenuators can be used to control amplitude. IC phase shifters or real-time delay circuits can be used to control phase. The actual time delay circuit can be quite simple; it involves routing a longer path to different antennas and controlling the specific length of the signal that must propagate. If the signal is fed from the same feed point, different path lengths will result in relative phase differences in the signal reaching the antennas, as shown in Figure 10(b).
(a) Controllable elements (b) True delay circuit
Figure 10. Array elements with separate amplitude and phase controls.
Considering the concept of wave interference, we can imagine how controlling the relative phase of the antennas can steer the main beam towards the desired direction, as shown in Figures 11 or below animations.
(a) Main beam at the end of the beam (b) Main beam at 45°
Figure 11. Controlling the main beam by controlling the relative phase of each antenna.
Electrically manipulating the main beam offers advantages over mechanical structures, saving costs, complexity, and providing resilience against mechanical failures. The rate of beam steering can be much faster than rotation systems. Although the ability to steer the main beam electrically provides significant advantages, the radiation pattern shape remains almost sinusoidal, with unwanted side lobes at high power levels.
Formation
We see that phase shifters can achieve steering, but the shape remains almost unchanged. In this section, we will show how to control the amplitude weighting of antenna units (Figure 12), thereby changing the shape of the radiation pattern.
Figure 12. Phased array representation
Linear Weighting
The radiation pattern in Figure 11 assumes an even distribution of weights on all antennas, as shown in Figure 13.
(a) Radiation mode (polar coordinates) (b) Even weight distribution
Figure 13. Polar coordinate radiation pattern with even weight distribution.
Hanning Distribution
If the weight distribution is not uniform but follows the Hanning distribution after equation 2 (as shown in Figure 14(b)), where antennas at the array center receive stronger signals than those at the edges, we can predict that patterns with sharper contours will be produced, as shown in Figure 14(a).
(a) Radiation pattern        (b) Hanning weight distribution
Figure 14. Radiation patterns from the polar coordinate system are based on the Hanning distribution.
Applying a weight distribution following the Hanning function in equation 2 will provide significantly higher directionality and significantly reduce the power dissipated in sidelobes.
Taylor Function
However, implementing a Hanning weight distribution is not straightforward. Instead, the Taylor distribution function is typically used. This DSP algorithm can be accessed through multiple sources. In MATLAB, the function taylorwin(N, nbar, sll) returns a weight distribution of N elements, where sll is the desired dB level of the nearest sidelobe, and nbar is the number of nearest sidelobes with sll value.
(b) Radiation directional pattern (b) Taylor weight distribution Taylorwin (32, 6, -40)
Figure 15. Polar coordinate radiation pattern of the Taylor weight distribution.
In cases similar to the Hanning function, the shape of the radiation pattern has slightly different contours but maintains the same expected characteristics: lower sidelobe levels.
Comparison
By comparing three weight distributions, we can see the differences in radiation directional patterns and main beamwidth. Depending on the application constraints, it may be necessary to consider widening the beamwidth as a design parameter. In any case, controlling the weight of the signal fed to each antenna can provide various desired radiation patterns according to the application.
(a) Overlapping radiation modes       (b) Close-up image of beamwidth
(c) Overlapping weight distribution function.
Figure 16. Three-dimensional comparison among uniform, Hanning, and Taylor weight distributions.
Disadvantages - Grating lobes
As with any other unique technology, there are always trade-offs that people should be aware of and manage properly. The multifunctionality of phased array antennas in terms of direction and shape does not mean zero cost. Grating lobes, as shown in Figure 17, are unnecessary and sometimes present due to signal mixing in phased array antennas. Grating lobes are not found on individual antennas because they are the result of an array arrangement.
Figure 17. Radiation diagram of grating lobes.
The precise explanation behind grating lobes goes beyond the scope of this article as it involves advanced topics in the field of signal processing and constraints on discrete processing and algorithms. Using the Nyquist Theorem in the time domain as a metaphor can provide a high level of understanding. As stated by Nyquist or sampling theorem: the sampling frequency required to reproduce the input signal must be twice the signal's frequency. Otherwise, aliasing occurs, and the output signal will distort. Using the same concept but in the spatial domain, if two adjacent antennas are positioned too closely together or too far apart from each other, the scanning of the signal will not lead to optimal scanning, given the relative phases of the received signals, and the overall radiation pattern will distort in the form of grating lobes. To avoid grating lobes in linear arrays, the distance between adjacent antennas should be between half a wavelength and full wavelength, as shown in Equation 3.
Recent applications - SpaceX's Starlink
One of SpaceX's latest missions is providing low-latency satellite internet worldwide. To achieve this, they have and will continue to launch thousands of satellites into low Earth orbit (Figure 18(a)). This is the first such scale project to provide global internet. Common satellites for providing internet are placed in geosynchronous orbit, where they can serve specific areas directed by the satellites (Figure 18(b)), because they rotate around the Earth at the same speed as it spins.
(a) Low Earth Orbit (b) Geosynchronous Orbit
Figure 18. Comparison of near-Earth orbit and geosynchronous orbit.
However, satellites placed in low Earth orbit will rotate faster than the Earth to maintain their orbit and thus provide services to different regions as they move. As shown in Figure 19, for continuous service, a Starlink constellation of satellites orbiting around Earth is needed to cover the required areas at all times.
Figure 19. Starlink Satellite Constellation [5]
Another point to note is that when the satellite rotates, signals sent from the satellite should reach the receiving stations. To achieve this, signals must be manipulated during the satellite's movement. As you might guess, Starlink satellites have four phased array antennas for signal transmission, as shown in Figure 20.
Figure 20. Starlink Satellites with Four Phased Array Antennas.
Finally, speaking on the topic:
In this article, we studied the advantages of phased array antennas over other single-antenna topologies, highlighting their ability to provide multifunctionality and control over radiation patterns. We also introduced the main drawbacks unique to this antenna topology: grating lobes. Finally, we discussed the current applications of phased array antennas with SpaceX's Starlink satellite constellation.
Before concluding this article, it's worth mentioning that phased array antennas are at the core of 5G and IoT (Internet of Things) technologies. Besides the multifunctionality highlighted in this article, phased array antennas support large-scale MIMO (Multiple Input, Multiple Output) communication capabilities, as shown in Figure 21(a). These antennas are also prevalent in new upcoming millimeter wave architectures (Figure 21(b)), and major companies have invested substantial resources and time in research and development of phased array antennas (Figures 21(c) and (d)). The development of communication systems has benefited greatly from these antenna topologies.
(a) Large-Scale MIMO Demonstration [10]   (b) IBM + Ericsson Millimeter Wave Prototype
Figure 21. Applications of Phased Array Antennas
Partial code display: %% Workspace variables\n% Range of azimuth angle (phi) and elevation (theta)\ndtheta = 0.1; %1 degree (in rad)\ntheta = -90:dtheta:90; %range of theta (-90 to 90 degrees)\ntheta_rad = deg2rad(theta); %theta in rads\ndphi = 2*dtheta; \nphi = -180:dphi:180; %range of phi (-180 degrees)\nphi_rad = deg2rad(phi); %phi in rads\n​\nN = 32; %number of elements\nfreq = 10e9; %10 GHz\nc = 3e8; %m/sec speed of light\nlambda = c/freq; %wavelength (m)\nk = 2*pi/lambda; %wavenumber (rad/m)\nd = lambda/2; %element spacing (m)\n​\nclose all           %clear all figures\nclc                 %clear command window\n​\n%% Part 1 -- Array Factor AF(theta) with Uniform Weighting Functions\nA_o = 1; %Standard element excitation\nA_n_uni = A_o.*ones(1,N); %element excitation weights\n​\ngamma = k*d*sin(theta_rad); %phase difference between adjacent elements @ boresight\n​\nEF_sum_uni = A_n_uni(1).*exp( 1j*(1).* gamma); %Element Field Factor @ n = 1\n​\nfor n = 2:length(A_n_uni)\n    el_factor = A_n_uni(n).*exp( 1j*n.* gamma); %Element Field Factor @ n\n    EF_sum_uni = EF_sum_uni + el_factor; %Total Field Factor @ n\nend\n​\nAF_uni = abs(EF_sum_uni).^2; %Array Factor (AF)\nAF_uni_nor = AF_uni./max(AF_uni); %AF normalized \nAF_uni_nor_dB = 10*log10(AF_uni_nor); %AF normalized in [dB]\nSimulation results\n        \n
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  
\n        \n  

## Images

![Phased Array Antenna [with MATLAB Code]](01.jpg)
![Phased Array Antenna [with MATLAB Code]](02.jpg)
![Phased Array Antenna [with MATLAB Code]](03.jpg)
![Phased Array Antenna [with MATLAB Code]](04.jpg)
![Phased Array Antenna [with MATLAB Code]](05.jpg)
![Phased Array Antenna [with MATLAB Code]](06.jpg)
![Phased Array Antenna [with MATLAB Code]](07.jpg)
![Phased Array Antenna [with MATLAB Code]](08.jpg)
![Phased Array Antenna [with MATLAB Code]](09.jpg)
![Phased Array Antenna [with MATLAB Code]](10.jpg)
![Phased Array Antenna [with MATLAB Code]](11.jpg)
![Phased Array Antenna [with MATLAB Code]](12.jpg)
![Phased Array Antenna [with MATLAB Code]](13.jpg)
![Phased Array Antenna [with MATLAB Code]](14.jpg)
![Phased Array Antenna [with MATLAB Code]](15.jpg)
![Phased Array Antenna [with MATLAB Code]](16.jpg)
![Phased Array Antenna [with MATLAB Code]](17.jpg)
![Phased Array Antenna [with MATLAB Code]](18.jpg)
![Phased Array Antenna [with MATLAB Code]](19.jpg)
![Phased Array Antenna [with MATLAB Code]](20.jpg)
![Phased Array Antenna [with MATLAB Code]](21.jpg)
![Phased Array Antenna [with MATLAB Code]](22.jpg)
![Phased Array Antenna [with MATLAB Code]](23.jpg)
![Phased Array Antenna [with MATLAB Code]](24.jpg)
![Phased Array Antenna [with MATLAB Code]](25.jpg)
![Phased Array Antenna [with MATLAB Code]](26.jpg)
![Phased Array Antenna [with MATLAB Code]](27.jpg)
![Phased Array Antenna [with MATLAB Code]](28.gif)
![Phased Array Antenna [with MATLAB Code]](29.png)
![Phased Array Antenna [with MATLAB Code]](30.png)
![Phased Array Antenna [with MATLAB Code]](31.png)
![Phased Array Antenna [with MATLAB Code]](32.png)
![Phased Array Antenna [with MATLAB Code]](33.png)
![Phased Array Antenna [with MATLAB Code]](34.png)
![Phased Array Antenna [with MATLAB Code]](35.png)
![Phased Array Antenna [with MATLAB Code]](36.png)
![Phased Array Antenna [with MATLAB Code]](37.png)
![Phased Array Antenna [with MATLAB Code]](38.png)
![Phased Array Antenna [with MATLAB Code]](39.png)
![Phased Array Antenna [with MATLAB Code]](40.png)
![Phased Array Antenna [with MATLAB Code]](41.png)
![Phased Array Antenna [with MATLAB Code]](42.png)
![Phased Array Antenna [with MATLAB Code]](43.png)
![Phased Array Antenna [with MATLAB Code]](44.gif)
![Phased Array Antenna [with MATLAB Code]](45.png)
![Phased Array Antenna [with MATLAB Code]](46.png)
![Phased Array Antenna [with MATLAB Code]](47.png)
![Phased Array Antenna [with MATLAB Code]](48.png)
![Phased Array Antenna [with MATLAB Code]](49.jpg)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
