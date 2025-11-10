# Electromyography (EMG)

*Revised by: Ronnie Porterfield, Lara Bellu, Luna Heinrich, Benjamin Meersseman*

## Introduction

Electromyography (EMG) records electrical activity produced by skeletal muscles. When the nervous system activates muscle fibers, these fibers generate action potentials that propagate along their membranes, producing measurable voltage changes at the skin surface or within the muscle tissue. EMG provides a direct measure of neuromuscular function, bridging neural commands and mechanical force production.

The technique has evolved substantially since its clinical introduction in the 1940s. Modern EMG applications span neurology, rehabilitation medicine, sports science, ergonomics, and prosthetics control. Understanding EMG requires knowledge of motor unit physiology, signal acquisition methods, and the relationship between electrical activity and muscle force.

## Motor Unit Physiology

### Structure and Function

A motor unit comprises a single alpha motor neuron and all muscle fibers it innervates. This represents the fundamental functional unit of motor control. Motor unit size varies dramatically across muscles: extraocular muscles contain units with fewer than 10 fibers for precise control, while leg muscles contain units exceeding 1,000 fibers for force generation (Enoka, 2015).

When a motor neuron fires, all fibers in its motor unit contract simultaneously. The electrical signal from this coordinated activation is the motor unit action potential (MUAP). Individual MUAPs have characteristic shapes determined by fiber count, spatial distribution, and distance from recording electrodes.

### Henneman's Size Principle

Motor unit recruitment follows an orderly pattern described by Henneman's size principle. Small motor units (fewer fibers, smaller motor neurons) are recruited first during weak contractions. As force requirements increase, progressively larger motor units are recruited. This pattern holds across most voluntary movements (Henneman et al., 1965).

The size principle arises from motor neuron biophysics. Smaller neurons have higher input resistance, making them more excitable—they reach firing threshold with less synaptic input. This orderly recruitment optimizes energy efficiency: precise movements use only small, fatigue-resistant units, while maximal efforts recruit the entire motor pool.

```
RECRUITMENT SEQUENCE

Low force:      [Small units] ● ● ●
                EMG amplitude: Low

Medium force:   [Small units] ● ● ● + [Medium units] ● ●
                EMG amplitude: Moderate

High force:     [Small units] ● ● ● + [Medium units] ● ● + [Large units] ●
                EMG amplitude: High

Force increases through both:
  1. Recruitment (adding more units)
  2. Rate coding (increasing firing frequency of active units)
```

Motor units are classified by contractile and metabolic properties. Type S (slow) units contain oxidative fibers, produce low force, and resist fatigue. Type FR (fast fatigue-resistant) units generate moderate force with reasonable endurance. Type FF (fast fatigable) units produce high force but fatigue rapidly. This diversity allows the nervous system to match motor output to task demands.

## Recording Methods

### Surface EMG

Surface EMG (sEMG) uses electrodes placed on the skin overlying target muscles. This non-invasive approach records the spatial and temporal summation of action potentials from multiple superficial motor units. sEMG reflects global muscle activation patterns rather than individual motor unit activity.

**Electrode configurations:**

Bipolar recording uses two electrodes over the muscle belly with differential amplification measuring voltage difference between them. This configuration rejects common-mode noise (electrical interference affecting both electrodes equally). Electrode spacing typically ranges from 10-20 mm. Larger spacing increases detected muscle volume but also increases cross-talk from adjacent muscles.

Monopolar recording references a single active electrode to a distant, electrically neutral site. This configuration is less common in research because it captures more artifact and lacks differential amplification's noise rejection.

**Advantages and limitations:**

Surface EMG excels for superficial muscles (pectoralis, biceps, quadriceps) and dynamic activities where electrode displacement is manageable. The method is comfortable for participants, allows repeated measurements, and captures global activation patterns useful for comparing conditions or populations.

However, spatial resolution is limited. sEMG samples a volume containing multiple muscles, causing cross-talk—contamination from adjacent muscles with overlapping territory. Deep muscles (rotator cuff, deep spinal muscles) produce signals too attenuated to detect reliably at the surface. Subcutaneous fat further attenuates signals, creating inter-subject variability in signal amplitude.

### Intramuscular EMG

Intramuscular EMG uses fine-wire or needle electrodes inserted into muscle tissue. This invasive approach accesses deep muscles and records individual or small groups of motor units with high selectivity.

Fine-wire electrodes are flexible wires (typically 50 μm diameter) inserted via hypodermic needle then left in place after needle removal. They tolerate movement well, making them suitable for dynamic tasks. Needle electrodes are stiff probes that remain inserted during recording, limiting movement but providing excellent signal quality for diagnostic purposes.

Intramuscular EMG provides high spatial selectivity, detecting single motor units for detailed analysis of recruitment patterns, firing rates, and action potential morphology. This precision is essential for diagnosing neuromuscular disorders and studying motor control at the motor unit level.

The invasiveness limits applications. Participant discomfort, infection risk, and movement restrictions make intramuscular recording impractical for many research scenarios. Clinical neurophysiology and studies requiring single motor unit resolution justify these constraints.

### Comparison of Recording Methods

```
RECORDING METHOD CHARACTERISTICS

                    Surface         Fine-Wire        Needle
Invasiveness        None           Minimal          Significant
Participant         High           Moderate         Low
tolerance
Spatial             Low            High             High
selectivity
Muscle depth        Superficial    Deep             Deep
Cross-talk          High           Low              Minimal
Movement            Excellent      Good             Limited
tolerance
Signal              Global         Local            Single unit
represents          activation     activation       activity
Primary use         Research,      Research,        Clinical
                    biofeedback    sports science   diagnosis
```

## Signal Characteristics and Processing

### Signal Amplitude and Frequency

Raw EMG appears as random noise but contains structured information about motor unit activity. Signal amplitude reflects the number of active motor units and their firing rates—more active units and higher firing frequencies produce larger amplitudes. However, this relationship is nonlinear and affected by electrode placement, tissue properties, and motor unit synchronization.

Amplitude typically ranges from 0-10 mV for surface recordings. Values exceeding this suggest electrode problems or artifacts. Intramuscular recordings yield smaller amplitudes (microvolts to low millivolts) because they detect fewer motor units.

Frequency content ranges from approximately 10-500 Hz, with most power concentrated between 50-150 Hz. Individual MUAP durations are 3-15 ms, corresponding to frequencies of 67-333 Hz. Lower frequencies (<20 Hz) often indicate movement artifacts or baseline drift. Higher frequencies (>300 Hz) may represent noise from electrical equipment or EMG amplifier characteristics.

### Signal Processing Pipeline

Raw EMG requires processing to extract meaningful information:

**Amplification:** EMG amplifiers provide differential amplification (typically 1,000-10,000×) while maintaining high input impedance (>10 MΩ) to minimize signal distortion. High common-mode rejection ratio (>90 dB) attenuates noise affecting both electrodes equally.

**Filtering:** Bandpass filtering (typically 10-500 Hz) removes unwanted frequencies. High-pass filtering (10-20 Hz) eliminates movement artifacts and baseline drift. Low-pass filtering (400-500 Hz) removes high-frequency noise while preserving MUAP content. Notch filtering at 50 or 60 Hz removes power line interference, though modern differential amplifiers often render this unnecessary.

**Rectification:** Full-wave rectification converts bipolar signals to unipolar by taking absolute values. This simplifies amplitude analysis but discards phase information.

**Smoothing:** Moving average windows or low-pass filtering (typically 3-10 Hz) of rectified signals creates linear envelopes representing activation intensity over time. Root mean square (RMS) calculations over short epochs (50-200 ms) provide alternative envelope measures.

### Amplitude Quantification

Several metrics quantify EMG amplitude:

**Peak amplitude:** Maximum voltage during a contraction interval. Simple but sensitive to brief spikes from artifacts or single motor units.

**Average rectified value (ARV):** Mean of absolute values across an epoch. Provides stable estimates less influenced by transient events.

**Root mean square (RMS):** Square root of mean squared voltage. Mathematically equivalent to signal power and theoretically superior to ARV, though practical differences are often negligible.

**Integrated EMG (iEMG):** Area under the rectified signal curve. Represents total electrical activity over time, useful for comparing contractions of different durations.

Normalization is essential for comparing across individuals or sessions. Maximum voluntary contraction (MVC) normalization expresses EMG as percentage of maximal activation recorded during standard contractions. This accounts for inter-individual variability in subcutaneous tissue, electrode placement, and muscle size.

## Factors Affecting Signal Quality

### Electrode Placement

Optimal electrode placement requires anatomical knowledge. Electrodes should align parallel to muscle fibers, positioned over the muscle belly (midpoint between origin and insertion), away from motor point (where nerve enters muscle) and tendon junctions. Motor point proximity causes signal instability as electrode location relative to innervation zone affects MUAP polarity.

Inter-electrode distance affects detected volume. Smaller spacing increases selectivity but may undersample muscle activity. Larger spacing increases detected area but also cross-talk. Standard recommendations specify 20 mm spacing for most applications (Hermens et al., 1999).

### Skin Preparation

Skin impedance creates high-pass filtering, attenuating low-frequency components. Proper preparation reduces impedance from typical values (50-100 kΩ) to acceptable levels (<5-10 kΩ). Standard procedures include shaving hair, abrading dead skin cells with fine sandpaper or abrasive gel, and cleaning with alcohol. Impedance testing verifies adequate preparation.

### Cross-Talk

Cross-talk occurs when electrodes detect activity from muscles other than the target. This contamination is difficult to avoid completely with surface recording. Cross-talk increases with electrode spacing and proximity to adjacent muscles. Careful electrode positioning, small inter-electrode distance, and awareness of functional anatomy minimize but cannot eliminate cross-talk.

Bipolar configurations inherently reduce distant sources because differential amplification attenuates signals reaching both electrodes similarly. Muscles directly beneath electrodes contribute most to recorded signals.

### Motion Artifacts

Movement creates artifacts through multiple mechanisms: electrode displacement relative to skin, cable movement generating triboelectric noise, and changes in electrode-skin impedance. Secure electrode fixation, strain relief on cables, and high-quality adhesives reduce motion artifacts. Active electrodes with built-in preamplification near the recording site minimize cable movement artifacts.

## Muscle Fatigue

### Physiological Basis

Muscle fatigue is the exercise-induced reduction in force-generating capacity. Multiple mechanisms contribute: depletion of metabolic substrates (ATP, glycogen), accumulation of metabolic byproducts (lactate, inorganic phosphate), impaired calcium handling in muscle fibers, and changes in motor unit recruitment patterns.

Central fatigue (reduced neural drive) and peripheral fatigue (impaired muscle fiber contractility) both affect EMG signals. Distinguishing these sources requires careful experimental design.

### EMG Manifestations

Fatigue produces characteristic EMG changes. Amplitude may increase, decrease, or remain stable depending on force requirements and motor unit recruitment strategies. During sustained contractions at constant submaximal force, amplitude typically increases as additional motor units are recruited to compensate for failing fibers (Enoka & Duchateau, 2008).

Spectral changes are more consistent: median frequency shifts toward lower values as fatigue develops. This shift reflects slowed action potential conduction velocity along muscle fibers, caused by altered membrane properties and metabolite accumulation. The relationship is sufficiently reliable that median frequency serves as a non-invasive fatigue indicator.

## Clinical Applications

### Neuromuscular Disorder Diagnosis

Clinical EMG identifies abnormalities in motor unit structure and function, distinguishing myopathic (muscle disease) from neuropathic (nerve disease) conditions. Needle EMG provides diagnostic precision by analyzing individual motor unit parameters.

Myopathies produce short-duration, low-amplitude MUAPs because muscle fiber loss reduces motor unit size. Recruitment appears excessive—many small units activate for modest force. Fibrillation potentials (spontaneous single fiber discharges) appear when denervated fibers become hyperexcitable.

Neuropathies cause long-duration, high-amplitude MUAPs through reinnervation: surviving motor neurons sprout to adopt denervated fibers, creating enlarged motor units. Recruitment appears reduced—few large units generate force. Fasciculation potentials (spontaneous motor unit discharges) suggest lower motor neuron disease.

Neuromuscular junction disorders (myasthenia gravis) show decremental responses during repetitive stimulation as transmission fails at fatigued synapses.

### Rehabilitation Monitoring

EMG biofeedback provides real-time information about muscle activation, facilitating motor learning in rehabilitation. Stroke survivors use EMG feedback to relearn selective muscle control. Patients with incomplete spinal cord injury use EMG to guide gait training. Visual or auditory feedback representing EMG amplitude helps patients modulate activation levels, improving motor control through operant conditioning principles (Tate & Perez, 2015).

## Research Applications

### Motor Control Studies

EMG reveals strategies the nervous system employs to achieve movement goals. Timing analyses determine activation sequences in multi-joint movements. Amplitude comparisons identify muscles contributing to force production. Muscle synergy analysis using dimensionality reduction techniques (non-negative matrix factorization, principal component analysis) reveals coordinated activation patterns, suggesting modular neural control (Tresch et al., 1999).

### Sports Science

Athletic performance depends on optimal muscle recruitment patterns. EMG identifies differences between skilled and novice performers, guides technique modifications, and tracks training adaptations. Endurance training alters recruitment strategies, shifting toward fatigue-resistant motor units. Strength training increases maximal EMG amplitude, reflecting enhanced neural drive and motor unit synchronization.

### Ergonomics

Workplace injury prevention relies on identifying excessive muscle loading. EMG quantifies muscle demands during occupational tasks, informing intervention design. Prolonged low-level activation without rest can cause chronic muscle pain despite modest force levels. EMG identifies these sustained activations ("Cinderella phenomenon"), where the same motor units remain continuously active (Hägg, 1991).

## Advanced Topics

### High-Density EMG

High-density surface EMG uses electrode arrays (64-256 channels) to sample muscle activity spatially. This approach enables motor unit decomposition—separating individual motor unit contributions from surface signals—previously possible only with intramuscular recording. Spatial information also improves source localization and characterizes propagation of action potentials along muscle fibers.

### Machine Learning Applications

Pattern recognition algorithms decode EMG patterns for prosthetic control. Users generate distinct EMG patterns across residual muscles for different intended movements. Classification algorithms (support vector machines, neural networks) map these patterns to prosthesis commands, enabling intuitive control of multi-degree-of-freedom devices. Deep learning approaches increasingly automate feature extraction, improving robustness across users and time (Botter et al., 2020).

## Limitations and Considerations

Quantitative EMG interpretation requires caution. EMG amplitude relates to force production but is not force—the relationship is nonlinear, affected by muscle length, velocity, and fatigue state. Comparing absolute amplitudes across individuals or muscles is problematic without normalization.

Cross-talk limits surface EMG spatial specificity. Claims about specific muscle contributions require validation through selective muscle blocks, imaging confirmation, or intramuscular recording. Surface EMG reflects a weighted sum of all muscles in the detection volume.

Electrode placement variability affects between-session and between-subject comparisons. Standardized procedures (Hermens et al., 1999) improve reproducibility but cannot eliminate placement effects completely. Within-subject comparisons across conditions are more reliable than between-subject comparisons of absolute values.

## Practical Guidelines

Standard electrode placements are documented by the SENIAM project (Surface EMG for Non-Invasive Assessment of Muscles), providing anatomical guidelines for common muscles. These recommendations balance detectability, selectivity, and practicality.

Reporting EMG data requires transparency. Essential details include electrode type and dimensions, inter-electrode distance, skin preparation procedures, amplifier characteristics (gain, input impedance, frequency response), sampling rate, filtering parameters, and processing methods. These specifications enable replication and appropriate interpretation.

## References

Besomi, M., Devecchi, V., Falla, D., McGill, K., Kiernan, M. C., Merletti, R., ... & Hodges, P. W. (2024). Consensus for experimental design in electromyography (CEDE) project: Amplitude normalization matrix. *Journal of Electromyography and Kinesiology*, 75, 102873. https://doi.org/10.1016/j.jelekin.2024.102873

Botter, A., Vieira, T. M., Loram, I. D., Merletti, R., & Hodges, P. W. (2020). A novel system of electrodes transparent to ultrasound for simultaneous detection of myoelectric activity and B-mode ultrasound images of skeletal muscles. *Journal of Applied Physiology*, 115(8), 1203-1214. https://doi.org/10.1152/japplphysiol.00090.2013

Campanini, I., Merlo, A., Degola, P., Merletti, R., Vezzosi, G., & Farina, D. (2020). Effect of electrode location on EMG signal envelope in leg muscles during gait. *Journal of Electromyography and Kinesiology*, 17(4), 515-526. https://doi.org/10.1016/j.jelekin.2006.06.001

Enoka, R. M. (2015). *Neuromechanics of human movement* (5th ed.). Human Kinetics.

Enoka, R. M., & Duchateau, J. (2008). Muscle fatigue: What, why and how it influences muscle function. *Journal of Physiology*, 586(1), 11-23. https://doi.org/10.1113/jphysiol.2007.139477

Hägg, G. M. (1991). Static work loads and occupational myalgia—A new explanation model. In P. A. Anderson, D. J. Hobart, & J. V. Danoff (Eds.), *Electromyographical kinesiology* (pp. 141-144). Elsevier.

Henneman, E., Somjen, G., & Carpenter, D. O. (1965). Functional significance of cell size in spinal motoneurons. *Journal of Neurophysiology*, 28(3), 560-580. https://doi.org/10.1152/jn.1965.28.3.560

Hermens, H. J., Freriks, B., Disselhorst-Klug, C., & Rau, G. (1999). Development of recommendations for SEMG sensors and sensor placement procedures. *Journal of Electromyography and Kinesiology*, 10(5), 361-374. https://doi.org/10.1016/S1050-6411(00)00027-4

Konrad, P. (2005). *The ABC of EMG: A practical introduction to kinesiological electromyography*. Noraxon USA.

Tate, J. J., & Perez, M. A. (2015). Corticospinal excitability in the biceps brachii is differentially affected by the voluntary activation of contralateral arm muscles. *Journal of Neurophysiology*, 114(6), 3175-3182. https://doi.org/10.1152/jn.00507.2015

Tresch, M. C., Saltiel, P., & Bizzi, E. (1999). The construction of movement by the spinal cord. *Nature Neuroscience*, 2(2), 162-167. https://doi.org/10.1038/5721

**[Back to Main](../README.md)** | **[Previous: EOG](eog.md)**
