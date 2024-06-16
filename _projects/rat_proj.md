---
layout: project
title: "Motion Planning Framework of Robotic-Rat for Behavioral Interaction"
authors:
  - name: "Mohamed Al-Khulaqui"
    url: "#"
  - name: "Guanglu Jia"
    url: "#"
  - name: "Hongzhao Xie"
    url: "#"
  - name: "Qing Shi"
    url: "#"
affiliations:
  - name: "Institute 1"
    logo: "/assets/img/rat_proj/bit.png"
abstract: >
  Robotic rats with bio-mimetic morphology and controllable movement patterns can replace real animals in behavioral interaction experiments and thus, have important research value in the biomedical field. Real-time generation of rat-like motions during interaction and stable and fast tracking of animals are necessary for autonomous behavioral interaction experiments. The current robots used for animal behavioral interaction experiments suffer from spatial inconsistency in motion data representation, low bio-mimetic similarity in motion expression, and poor motion control tracking ability. In this work, we propose a data-driven motion planning method for the behavioral interaction of the bionic robot mouse SMuRo, and realize real-time tracking of the laboratory rat and bio-mimetic motion generation for the robotic rat during the interaction.
---

<div class="section">
    <h2>Lab Rat Motion Data</h2>
    <p>
        In order for the robotic-rat to produce rat-like motions, lab rat motion data is gathered and classified
        into multiple behavioral patterns forming a lab rat motion dataset. Markers are placed on the rat's spine
        to capture the spine contour curve of the rat. The position of the markers was chosen based on Key Movement
        Joint (KMJ) analysis previously done by our team.
    </p>
    
    <div class="image-section">
        <div class="image-container">
            <img src="/assets/img/rat_proj/key-movement-joints.png" alt="Key movement joints" class="image">
            <div class="image-caption">Key Movement Joints</div>
        </div>
        <div class="image-container">
            <img src="/assets/img/rat_proj/motion-capture.png" class="image">
            <div class="image-caption">Motion capture setup</div>
        </div>
    </div>
</div>

<div class="section">
    <h2> Motion Retargeting</h2>
    <p>
        Due to difference in motion space between the motion data and the joint space of the robotic rat,
        a mapping relationship between them needs to be established.
        
        We propose a mapping method that finds the joint angles of the robotic rat that correspond
        to a certain spine configuration by minimizing the Euclidean distance between the spine contour
        curves of both rats. 
        
        Thus, the mapping problem is formualted as a nonlinear curve fitting optimization problem, 
        and is used to convert the rat motion data to the robotic rat joint space under different behavioral
        patterns.

        The resulting is evaluated using cosine similarity, which showed a minimum of 96% similarity between both contours.
    </p>

    <img src="/assets/img/rat_proj/mapping_process.png" alt="Mapping process" style="width: 800px; height: auto;">
    <div class="image-caption">Spine Contour Formulation Process</div>
    <h5>Mapping Results</h5>
     <div class="video-section">
        <div class="loop-video-container">
            {% include video.liquid path="/assets/video/MO1.mp4" autoplay=true muted=true loop=true caption="MO 1" type="video/mp4"%}
        </div>
        
        <div class="loop-video-container">
            {% include video.liquid path="/assets/video/MO2.mp4" autoplay=true muted=true loop=true caption="MO 2"  type="video/mp4"%}
        </div>

        <div class="loop-video-container">
            {% include video.liquid path="/assets/video/PIN1.mp4" autoplay=true muted=true loop=true caption="PIN 1"  type="video/mp4"%}
        </div>

        <div class="loop-video-container">
            {% include video.liquid path="/assets/video/PIN1.mp4" autoplay=true muted=true loop=true caption="POU 1"  type="video/mp4"%}
        </div>

        <div class="loop-video-container">
            {% include video.liquid path="/assets/video/SNC1.mp4" autoplay=true muted=true loop=true caption="SNC 1"  type="video/mov"%}
        </div>

        <div class="loop-video-container">
            {% include video.liquid path="/assets/video/SNC2.mp4" autoplay=true muted=true loop=true caption="SNC 2" type="video/mp4"%}
        </div>
    </div>
</div>

<div class="section">
    <h2> Motion Modeling</h2>
    <p>
        Probabilistic Motion Primitives are used to model the motions of each behavioral pattern from the mapped dataset.
        The randomness of Gaussian models allows us to construct a probabilistic model with a distribution
        consistent with that of the laboratory rat motion data in order to generate motion trajectories in
        the joint space of the robotic rat that follow the same patterns. 
    </p>

    <div class="image-section" >
        <div class="image-container">
            <img src="/assets/img/rat_proj/ProMP.png" class="image">
            <div class="image-caption"> Gaussian Basis Functions </div>
        </div>
        <div class="image-container">
            <img src="/assets/img/rat_proj/ex-joint-trajectory.png" class="image">
            <div class="image-caption"> Example Joint Trajectory</div>
        </div>
    </div>
    
    <img src="/assets/img/rat_proj/promp-joint-trajs.png" class="image" style="width: 800px; height: auto; margin-top: 50px;">
    <div class="image-caption"> Estimated Motion Distributions</div>
</div>

<div class="section">
    <h2> Target Tracking</h2>
    <p>
        A rat tracking algorithm using Image-Based Visual Servoing (IBVS) is proposed. By deriving
        the interaction matrix and the robot jacobian, a Task Jacobian is constructed to model the 
        mapping relation between the tracking error in pixel coordinates and the joint angles in joint 
        space of the robotic rat. The algorithm achieves fast and stable real-time target tracking and 
        outperforms a previously used rule-based algorithm. Finally, mock behavioral interaction 
        experiments are conducted to verify the validity of the proposed methods.
    </p>

    <img src="/assets/img/rat_proj/vs-tracking.png" class="image" alt="vs-tracking" style="width: 800px; height: auto;">
    <div class="image-caption"> Image-Based Visual Servoing </div>

    <div class="video-section">
        <div class="video-container">
             <video controls muted playsinline>
                <source src="/assets/video/Rat-tracking.mp4" type="video/mp4">
            </video>
            <div class="video-caption">Target tracking</div>
        </div>
        
        <div class="video-container">
            <video controls muted playsinline>
                <source src="/assets/video/social-exp.mp4" type="video/mp4">
            </video>
            <div class="video-caption">Mock Interaction Experiment</div>
        </div>
    </div>
</div>
