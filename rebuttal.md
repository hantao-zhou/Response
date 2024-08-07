# Robogolf rebuttal

## Reviewer mxRY (wr, confidence:3)

Thank you for your comments and suggestions, the detailed responses regarding each problem are listed below. We hope to resolve the misunderstandings caused by the imperfection of our presentation. If you have any other questions, please post them and we are happy to have further discussions.

> **W1: Lack of a Baseline: The authors do not compare their method to other techniques that can be used to perform the same task. Even though there might not be any methods that have been evaluated on playing miniGolf, this work could have been compared to approaches that have been used to play similar sports [1, 2].** 

Thank you for highlighting these interesting works.

However, directly applying them to minigolf challenges is problematic. Their methods, as described in their original papers, are confined to simple, obstacle-free courts, which match the toy cases in our experiments. Note that our primary experiments focus on scene understanding and active modification involving numerous obstacles, exceeding the capabilities described in these works.


Additionally, neither of these works provides public code, and there are significant differences in hardware settings. Therefore, attempting to implement them within the rebuttal period is impractical and unnecessary.




Nonetheless, we acknowledge they might offer alternative solutions for the toy case experiments. We expanded our related works to include discussions with these methods as follows, which does not diminish but further highlight our contribution.

"Although there exist prior works exploring golf sport with robotic arms[1-2], most of them focuses on devising hitting devices and hitting mechanisms，thus they could only handles toy case court layout without any obstacles. In contrast, our work proposes a framework that could understand various court layouts, planning possible routes and actively provide court modification suggestions."


[1] Xu, Chunquan, et al. "Motion control of a golf swing robot." Journal of Intelligent and Robotic Systems 56 (2009): 277-299.

[2] Junker, Annika, et al. "Autonomous golf putting with data-driven and physics-based methods." 2022 Sixth IEEE International Conference on Robotic Computing (IRC). IEEE, 2022.



> **W2: _Clarity of Writing_: This paper was a little hard to follow. Since so many existing components have been combined to develop the system, the details about which models were fine-tuned with what data and which models were used in a zero shot manner were hard to find. Moreover, most details about the data and the models were in the supplementary material, forcing me to go back and forth between the main paper and supplementary material made it difficult to keep track of the big picture of the paper. This also made it hard to determine if any novel components were introduced or any models were trained. In a similar vein, the authors should explicitly state the contributions of their paper explicitly in the introduction.**


Thank you for your suggestions. Due to page limits, we initially placed the implementation details in the Appendix, prioritizing space for the overall framework design and experiments. We will integrate key implementation details from the Appendix into the main paper. 

And per your suggestion, we added a paragraph in the introduction to explicitly highlight our contributions. We have clearly stated our contributions as the proposal of the framework and implemented in a physics-based scenario.



> **W3: _Results and Ablation_: In this paper, the authors mostly focused on qualitative results over quantitative results. While the qualitative results look impressive, the basic quantitative metrics were provided as checks and crosses in Figure 4, which were very easy to miss. Also, their quantitative metrics do not provide a very good measure of the system performance. The authors should provide aggregate system-level performance metrics over all difficulty levels. Additionally, the ablation study described in the supplementary material is also very qualitative and does not provide a measure of how much each component adds to the overall performance.**


We appreciate your acknowledgment of our qualitative results and thank you for your suggestions. We will convert the checks and crosses into a table for clearer presentation.

**Regarding metrics on hitting outcomes and court analysis**, which are our main focuses:
* Actually prevous works fall short in providing quantitative metrics, [1] does not provide any quantitative results regarding hitting outcomes and course analysis, while [2] includes only one example. 
* In our work, 1) for successful hits after inner closed-Loop refinements, we opt for both quantative and qualitative metrics to demonstrate this, 2) for court modification suggestions: we show the qualitative modifications suggested by RoboGolf.

**Regarding other aggregate system-level performance metrics**: Unlike the works [1] and [2] suggested by the reviewer, our focus is not on hitting motion design or hardware design, which only serve as underlying tools for our system. Therefore, we do not present aggregate system-level performance metrics, such as pseudo energy, angle, angular velocity, stroke velocity, control input, or head speed, as they are out of the scope of our work.

We warmly welcome other possible suggestions regarding other suitable system-level performance metrics, which may much help to enhance our paper.


**Regarding ablation studies**: Actually, without each component design of RoboGolf, the framework would not function at all, leading to a zero success rate. Hence, qualitative results are better suited to show the detailed differences and importance of each component.



> **W4: _Reflective Equilibrium_: The concept of reflective equilibrium is neither explained in a paper in a grounded manner nor it is explained how it has been used as a part of their algorithm.**

Thank you for your comment. 

Reflective equilibrium represents the high-level intelligence we aim to achieve. We introduce the concept of reflective equilibrium and its manifestations in robotic tasks in Lines 27-34.

To achieve this level of intelligence, we propose the outer loop of our RoboGolf system, equipped with a fine-tuned counterfactual VLM. This allows it to evaluate the feasibility of tasks and actively provide modification suggestions, thereby achieving reflective equilibrium in minigolf challenges.

In essence, reflective equilibrium serves as the guiding intelligence to inspire our algorithm, rather than a technique used in our algorithm.



> **Q1: The authors should clarify what is the intended contribution of their work. Do they claim to have a novel system or are any of the components of the model novel?**

Per your suggestion, we provided a paragraph in Introduction section to explictly clarify the contribution of our work.

In short, 1. We propose a nested closed-loop framework capable of autonomously generating suggestions while accounting for constraints in a reflective equilibrium manner. 2. We design and implement this framework using a fine-tuned Visual-Language Model (VLM) and customized sensors, specifically tailored for the kinodynamic understanding task in minigolf. 3. We demonstrate the effectiveness of our framework and its implementation through extensive experimental validation.

> **Q2:The authors should provide concrete quantitative results of their ablation study.**

Actually, qualitative results are more effective in demonstrating the detailed differences and significance of each component, as explained in our response to **W3**. 

Without the complete design of each component in RoboGolf, the framework would fail entirely, resulting in an identical zero success rate across all ablation studies. To elaborate, without fine-tuned VLMs, implementing RoboGolf with the vanilla GPT-4V could not produce correct planning and evaluations, as shown in Appendix F.2. Furthermore, without the perception module, RoboGolf would not function at all.




> **Q3: The authors should implement or justify the lack of an external baseline.**

For component comparison, we have compared to the popular GPT-4V to show the effectiveness of our two fine-tuned VLMs, as shown in Appendix F.2.

Regarding the whole system and task definitions, the suggested previous works could not handle our tasks except for the toy cases, as elaborated in our response to **W3**.



> **Q4: The authors should compare their work with literature with work that uses robots to play similar sports that involve using a club or a bat to swing a ball through obstacles.**

Thank you for your suggestions. We extened our related works to include discussions and comparisons with previous works playing golf, as detailed in our response to **W1**.


> **Q5: The authors should better ground their work to the concept of reflective equilibrium.**

Per your suggestions, we added the following explanations to better readability. 


"In minigolf tasks, reflective equilibrium intelligence means that the robot will not blindly attempt to solve the human-assigned tasks. Instead, it will evaluate whether a feasible solution exists for the given court layout. If it deems the task impossible, the robot can actively provide suggestions to the human on how to remediate the infeasibility."

> **Q6: The authors should consider restructuring the paper to make it easier for the reader to follow the different components without going back and forth between the main paper and the supplementary material.**

Due to page limits, we initially arranged the implementation details in the Appendix. We will integrate key implementation details from the Appendix into the main paper based on your suggestions.


> **Q7: The authors should include a supplementary video of their system with both success and failure cases of their method for courts of various difficulty levels.**

Thanks for your suggestions, now we provide several failure cases of our methods in xxxx. 

==Add videos: zip file放或者repo放都可以==

> **Q8: The authors should explicitly state the limitations of their work in the main paper. To make space for this, the authors could consider moving some of their figures to the supplementary material.**

We initially mention some limitations of the entire experiment, regarding the current human intervention that makes the full work not entirely autonomous in Lines 240.

And thank you for your suggestions. We have now explicitly combined these points into a dedicated Limitation section in our paper. In this section we mentioned our major limitations of generalizability, difference from actual world complex kinodynamics tasks and lack of quantitative results.



Thanks again for your comments. We will be continued to polish our statement for clarity in our revision. Thanks again for your comments and we wish you could reconsider your score. 


# Reviewer HbSW (wa, confidence:4)

> **W1:** "Intelligence" Definition: Claims regarding the system's "intelligence" should be carefully considered and presented using more moderate language. The gap between the capabilities of technical systems and human intelligence needs to be accurately reflected.

Thank you for your suggestion. We acknowledge that there is a gap between technical systems and human intelligence. We initially used this term following some popular and classical works [1,2,3,4] that also aim to devise smart systems for tackling robotic tasks.

The reflective equilibrium "intelligence" serves as the inspiration and target for our system. We now clearly stated that such intelligence is a guiding principle, not an actual achievement. 

limitations are mentioned in the final section of the limitations.

[1] Hu, Yingdong, et al. "Look Before You Leap: Unveiling the Power of GPT-4V in Robotic Vision-Language Planning." First Workshop on Vision-Language Models for Navigation and Manipulation at ICRA 2024.
[2] Mai, Jinjie, et al. "Llm as a robotic brain: Unifying egocentric memory and control." (2023).
[3] Wang, Jiaqi, et al. "Large language models for robotics: Opportunities, challenges, and perspectives." arXiv preprint arXiv:2401.04334 (2024).
[4] Fu, King Sun, et al. Robotics: control, sensing, vision, and intelligence. Vol. 1. New York: McGraw-Hill, 1987.




> **W2.** 1. **Comprehensive Video Demonstrations:** Providing more comprehensive video demonstrations would significantly enhance the paper's impact and allow for a more thorough assessment of RoboGolf's performance. Consider including:
> 	1. **Isometric View Video:** This would showcase the entire environment and system operation simultaneously.
> 	2. **Full-Screen Video:** This would focus on the robot's actions and the ball's trajectory, providing a detailed view of the system's performance.

Thanks for the advice, our current video can well demonstrate the entire environment and system operation simultaneously. It is hard to present isometric view video within limited time. The full-screen video has been provided for a detailed view of the system's performance in the repo.


> **W3: Terminology and Method Naming: The concept of "reflective equilibrium" serves as inspiration for your approach, but it might not be the most fitting terminology within the robotics domain. Consider exploring and justifying the use of more common robotics terms, such as "self-evaluation," "task adaptation," or "constraint-aware planning." To enhance clarity, propose a unique and technically descriptive name for your specific method, distinguishing it from the broader concept of "reflective equilibrium."**


Actually, in our paper, "reflective equilibrium" serves as the inspiration from human intelligence, while "counterfactual reasoning", represents its manisfestation in robotics. We have revised our paper to better clarify this distinction.


We agree that the other common robotics terms you suggested, such as "self-evaluation," "task adaptation," and "constraint-aware planning," are excellent expressions. However, none of them individually capture the full essence of "reflective equilibrium" in our context.

Specifically, in the minigolf scenario, the robot needs to not only self-evaluate its performance but also assess the task itself and proactively suggest modifications to the courts to make them feasible. "Task adaptation" and "constraint-aware planning" focus on spatial and kinodynamic understanding, whereas "counterfactual reasoning" best describes the spectrum of reflective evaluation.





> **W4: Human and Robot Baseline Comparisons:** Incorporate a comparison with both a human baseline and other robot baselines, as in:
> 1. Mnih et al. [r1], which is an example of how to incorporate a human-level baseline.
> 2. Khansari-Zadeh et al. [r3], which is prior work on a minigolf playing robot.
> 3. Alternatively, rigorously justify why this cannot be done to provide a clear performance benchmark and establish the system's capabilities relative to existing approaches.


While incorporating a comparison with a human baseline and other robot baselines would undoubtedly be beneficial, we found it unsuitable in our case after extensive search and evaluation.

Regarding Mnih et al.'s work, they used professional human players as baselines. For our work:

* Minigolf is not a standardized game like Atari, making it challenging to establish a suitable human baseline. We attempted to play the game ourselves, but it is difficult for untrained individuals to accurately estimate parameters and consistently refine them based on historical data.
* Hiring professionals in the field of minigolf to complete this task is cost-prohibitive.

Regarding the work of Khansari-Zadeh et al.:
* The hardware and settings are significantly different from ours. They focus on special terrains, whereas our focus is on understanding complex court layouts, planning, and modifications.
* Additionally, their work does not come with public code, making it difficult to replicate their work within rebuttal phrase.




> **W5:** 
> 1.Expanded Discussion of Limitations: A dedicated section is required to thoroughly address the limitations of the current system. 
> 2. Specific Points to Include:
> * Simplified Assumptions: Acknowledge and discuss any simplifications or assumptions made regarding the environment or task complexity.
> * Model Limitations: Discuss limitations inherent to the VLMs or other models used, such as potential biases or failure modes.
> * Runtime Performance: Analyze the computational complexity of the proposed method, including the time required for VLM inference, control loop iterations, and overall system response. Discuss the implications for real-time performance and deployment in real-world settings. 
> * Potential Sources of Error: Identify potential sources of error in perception, control, and decision-making, and analyze their impact on overall system performance.
> * Constructive Insights and Future Directions: This section should also offer constructive insights into potential avenues for improvement and guide future research directions.

We initially mention some limitations of the entire experiment, regarding the current human intervention that makes the full work not entirely autonomous in Lines 240. And we have discussed constructive insights and future research directions in the conclusion section in our original paper.

And thank you for your suggestions. We have now explicitly combined these points into a dedicated Limitation section in our paper. In this section we mentioned our major limitations of generalizability, difference from actual world complex kinodynamics tasks and lack of quantitative results.







> W6: 1. "Real-World" Claims: It is essential to acknowledge that the experimental setting, while physical, is a controlled lab environment, which differs significantly from real-world minigolf courses.
    1. Deployment Challenges: Discuss the specific challenges and considerations for deploying RoboGolf in uncontrolled real-world settings. Consider factors such as variations in lighting, terrain, and potential obstructions (e.g., other players, objects).


Thanks for the suggestions. 

We now acknowledge that our current setup is within a controlled lab environment. But, compared to other related papers on minigolf and golf, ours is the first to successfully navigate complex obstacle scenarios, offering significant insights for advancing robotics in this sport towards real-world applications.

We now included a paragraph discussing the specific deployment challenges.
* The variations in lighting can pose challenges for our perception module. Fortunately, YOLO and SAM in our perception module demonstrate robustness to changes in lighting conditions when encoutering no significant exposure issues.

* The variations in terrain present a complex issue, as they can greatly affect kinodynamics. Therefore, VLMs fine-tuned on completely different terrains cannot be directly applied; further data collection and fine-tuning of VLMs are necessary on the current terrain.

* Potential obstructions, such as other players, are dynamic and unpredictable obstacles. This poses a challenging issue, especially in our current single-hole setup, where such dynamic obstacles are not addressable. Exploring multi-hole scenarios could be a promising direction for future work.






> W7: **Expanded Prior Work Discussion:** The current discussion of prior work is insufficient. 
    1. **Include:** Research on golf robots and minigolf robots, particularly those incorporating learning-based methods, such as the work by Khansari-Zadeh et al. [r3].
        2. **Dynamics Learning:** Consider incorporating prior work on dynamics learning for robot manipulation, such as Zeng et al.'s TossingBot [r2].


Due to page limits, we initially prioritized prior works related to VLM in robotics and kinodynamic understanding, which are our main focuses.

Per your suggestions, we now expanded our related works section to encompass research on both golf robots and minigolf robots.

In our original paper, we have discussed several works on dynamics learning for robot manipulation from Lines 57 to 66. We appreciate your suggestion and have now included TossingBot in our revised version.






> W8: 1. **Expanded Ablation Study:** Provide a more comprehensive and quantitative ablation study to thoroughly analyze the impact of each system component.
> 2. **Quantify:** The performance impact (e.g., success rate, number of attempts) of:
    1. The nested closed-loop design (with and without inner/outer loops).
        2. The fine-tuned VLMs compared to alternative VLMs or baseline methods.
        3. The use of topography information.
    2. **Include specific results and quantitative metrics to support your findings.**

Without each component designed for RoboGolf, the framework would fail completely, resulting in a zero success rate. Therefore, qualitative results are better suited to illustrate the detailed differences and importance of each component, as outlined in Appendix F.

* RoboGolf can function in feasible courts even without the outer loop, as demonstrated in Figures 4 and 5. The outer loop is specifically designed to handle impossible scenarios and provide modification suggestions, as depicted in Figures 6 and 7. Conversely, without the inner loop, RoboGolf cannot effectively plan and control, as only the inner loop can generate hitting parameters.
* Using the standard GPT-4V for RoboGolf consistently results in failure, leading to a zero success rate. Therefore, we have included a detailed qualitative comparison with GPT-4V in Appendix F.2.
* Topographical information is crucially captured by depth data. Without such information, RoboGolf would be unable to navigate pathways beneath obstacles (see Part 1 in Figure 7), identify changes in bridge heights, or locate holes, among other essential tasks.

While the prospect of providing quantitative metrics to support our findings is appealing, it is currently impractical to do so based on performance metrics, as all ablation studies yield identical zero results. We welcome any reasonable suggestions from the reviewer regarding appropriate quantitative metrics.




> **W9: System Design Graphic: Include a more detailed, high-level graphic illustrating the overall system design. This visual representation will help readers grasp the system's architecture and the interactions between its components, such as the dual-camera setup, VLMs, and control loops.**


We did provide system design graphics ranging from high-level overviews to detailed illustrations. 
* Figure 1 presents a high-level illustration of the overall framework, depicting the architecture and interactions of its components. 
* Figures 2 and Figure 10 detail the perception module, including the camera setup
* Figures 6 and Figure 9 provide comprehensive insights into the workings of VLMs and control loops.


> **Q1:** Generalizability:
    1. Have you considered experiments or analyses to assess the generalizability of RoboGolf to more complex minigolf scenarios? For example, scenarios with more complex terrain. 
        2. What are your initial findings or plans in this regard?
        3. What are the key challenges in adapting the RoboGolf system to other real-world robotic tasks? Especially those requiring similar reasoning, manipulation skills, and adaptability.

1. Through abundant experiments spanning various combinations, types, and arrangements of obstacles and endpoints, we have effectively demonstrated the generalizability of our RoboGolf. We appreciate the proposal to explore different terrains for future directions. As detailed in our response to **W6**, collecting corresponding data from target terrains and using it to fine-tune our VLMs will enhance RoboGolf's compatibility across different terrains.

2. Our initial findings underscore that the generalizability of VLM-based methods heavily depends on the training and fine-tuning data. If the required knowledge isn't captured in the training data, the VLM will struggle to handle it, rather than vice versa. Moving forward, expanding RoboGolf to different terrains presents a promising avenue for future work.

3. For detailed insights into deployment challenges, please refer to our response to **W6**.





> **Q2:** **Quantitative Analysis:**
    1. Can you provide more detailed quantitative results, including specific metrics and comparisons, particularly execution time, to demonstrate the effectiveness of the nested closed-loop design and the fine-tuned VLMs?
        2. How does the performance of the system, measured in terms of success rate and efficiency (e.g., time to complete a course), differ when either the inner or outer control loops are deactivated?
        3. What specific metrics did you use to evaluate the quality and accuracy of the VLM's reasoning and planning outputs? For example, did you compare the VLM's planned trajectories with the actual ball trajectories?

1.We have provided sufficient quantitative results to demonstrate the effectiveness of the framework. Previous works fall short in providing quantitative metrics: [1] does not provide any quantitative results regarding hitting outcomes and court analysis, while [2] includes only one example. In contrast, for successful hits after inner closed-loop refinements, we opt for both quantitative and qualitative metrics to demonstrate this.
For court modification suggestions, we show the qualitative modifications suggested by RoboGolf. For further quantitative results, it is implausible to provide due to the lack of standardized benchmarks. As for the execution time, it is not related to the core topic of this paper, as we don't target the time efficiency of the VLM models.


2.Regarding other aggregate system-level performance metrics: It is simply implausible yet meaningless to provide measurements of execution without the frameworks, as the inner-loop is in charge of improving hitting mechanism, the outer-loop is in charge of counterfactual thinking and autonomously providing suggestions. Leaving any of these will lead to total failure.

3.The VLM is finetuned based on the LLAVA finetunning process as mentioned in line 152-153 and appendix B.2, naturally the evaluation of the VLM is the same as evaluating the LLAVA. The comparison of the LLAVA's plan and the actual execution result should not be considered as an evaluation of the VLM, as it is exactly what we considered in the inner closed-loop design, the difference between image prediction and real-world physics. Which is a part of the goal of our framework design.



> **Q3** **"Reflective Equilibrium:"**
     1. Can you elaborate on the specific advantages of framing the outer loop as "reflective equilibrium"?
         2. How does this concept provide unique benefits compared to alternative terms like "self-evaluation" or "task adaptation"?
         3. How does RoboGolf's implementation of "reflective equilibrium" compare to other robotic systems that incorporate self-evaluation or adaptation mechanisms?
          4. Are there any notable similarities or differences in the approaches?
        5. Will you select a term that distinguishes your technical approach from the general concept of "reflective equilibrium"?


1. In our paper, 'reflective equilibrium' serves as inspiration from human intelligence. Currently, most robotics approaches blindly follow user instructions, resorting to trial and error for infeasible tasks. 'Reflective equilibrium' inspires us to imbue robots with counterfactual reasoning, enabling them to suggest adjustments to make tasks feasible beyond their current capabilities. We believe developing this ability can enhance robots' intelligence and adaptability in open-world scenarios.

2. As exlaborated in our response to W3, 'reflective equilibrium' and its manifestation in robotics as 'counterfactual reasoning' encompass a broader spectrum of abilities. In contrast, 'self-evaluation' represents one aspect, while 'task adaptation' relies more on spatial and kinodynamic understanding capabilities.

3&4. Our RoboGolf not only conducts self-evaluation of its performance but also evaluates the task itself, actively proposing modifications to the courts to ensure feasibility. In contrast, 'self-evaluation' alone does not actively suggest concrete modifications, and 'task adaptation' primarily pertains to the inner-loop of our RoboGolf rather than the outer-loop.

5. Indeed, we used 'counterfactual reasoning' to exemplify the manifestation of 'reflective equilibrium' in robotics within our original paper.




> **Q4** Real-world Deployment:
    1. What concrete modifications or additions would be required to facilitate the transition of RoboGolf from its current lab setting to a real-world minigolf course?
    2. How do you envision the system handling variations in lighting, terrain, and other environmental factors commonly encountered in uncontrolled real-world settings? For example, would you need to retrain the VLMs with data from real-world courses to improve robustness?


Thanks for the suggestions. 
As detailed in our responses to W6, we now added a paragraph discussing specific deployment challenges such as variations in lighting, terrain, and potential obstructions.

Our perception module demonstrates robustness to lighting variations, supported by the resilience of YOLO and SAM utilized. Regarding terrain variations, we acknowledge the necessity of retraining VLMs with data specific to the target terrain to enhance robustness.

Thanks again for reading our article carefully and giving very constructive suggestions. We hope that the above can resolve your concerns and we are glad to have further discussion.





# Reviewer BpH7 (wr, condifidence:2)


> **W1&Q2 1. Notation Confusion:
    - The use of various notations (e.g., FVLM,FVL,Fv,Fθ,Fe,Fr) without sufficient explanation makes it difficult for readers to follow the methodology.
    - Each notation should be clearly defined and explained in the context of the framework to avoid confusion.
	2. **Explanation of Notations and Methods:**
    - Provide a detailed explanation of line 128 ( L121 and L131).
    - Clarify what ( F_v ) represents and whether it is a policy model.
    - Include details on how the policy model ( F_v ) was trained.**


Thank you for your suggestions. We now revised our maniscript to ensure sufficient explanations for each notation and method. 

**Notation clarification :**
In this context, all $\mathcal{F}$ functions represent VLMs (Visual-Language Models) adopted in different manners. $\mathcal{F}_{VG}$ denotes the visual grounding VLM, specifically LISA in this scenario. The other subscripted functions represent fine-tuned VLMs with distinct purposes, such as route planning (route), evaluation (e), and parameter refinement (r). The process of training the VLM is shown below.

**Training details of $F_v$ :**
The training process of $F_v$ is same as other F with subscripts, they are the finetuned VLM, the added explanation details as follows:

Methodologically, as described around line 139, the model is constructed based on fine-tuning a Visual-Language Model (VLM) to enhance its specific capabilities. We specifically adopted LLAVA as the fine-tuning backbone around line 152, refining it with our dataset. The validation of the model is integrated into the LLAVA training procedure, ensuring training effectiveness according to NLP standards. The training regimen consists of a single epoch with a batch size of 16 per device, utilizing the deepspeed library for acceleration. The learning rate is set to 2e-5, with no weight decay and a warmup ratio of 0.03. A cosine learning rate scheduler optimizes the training process over time. During training, although the model is not evaluated, the process is logged at every step, and the model is saved every 50,000 steps, retaining only the last checkpoint. The training is meticulously tracked and visualized using Weights & Biases, providing detailed insights into the model's performance. This comprehensive training regimen is designed to optimize the model's performance for the task while offering a transparent view of the training process.




>**W2. Lack of Quantitative Results:
    - The paper lacks quantitative results, making it challenging to evaluate the performance and robustness of the proposed framework comprehensively.
    - Including metrics such as success rates, error rates, and performance comparisons with other methods would provide a more complete assessment of the framework's effectiveness.**

We have included quantitative results through cross and check marks in Figure 4, which indicate the success or failure of each attempt.

Regarding the performance of the whole framework, there are currently very few studies on similar tasks. Two studies focus on playing golf [1-2], but they can only handle toy case court layouts without any obstacles.

For the performance of each component, removing any component results in complete failure, leading to identical quantitative results of zero. Therefore, we opted for qualitative results to better observe the differences and importance of each component, as shown in Appendix F.2.

[1] Xu, Chunquan, et al. "Motion control of a golf swing robot." Journal of Intelligent and Robotic Systems 56 (2009): 277-299.

[2] Junker, Annika, et al. "Autonomous golf putting with data-driven and physics-based methods." 2022 Sixth IEEE International Conference on Robotic Computing (IRC). IEEE, 2022.




>  **w3 & q1: Insufficient Method Details:**
> - The paper does not provide enough detailed explanations of certain methods and processes, such as how prompt SAM is used, how information from the RGB-D and event cameras is integrated, how LISA identifies the endpoint g, and how GPT-4V generates a reasonable route r from start s to endpoint g.
> - More detailed methodological explanations are needed to enhance clarity and allow for replication of the study.**
> **Clarity of Descriptions:** Some descriptions in the paper are unclear, leading to confusion. Specific areas that need clarification include:

> - How the authors use prompt SAM.
> - How information from the RGB-D camera and event camera is composed.
> - How LISA is used to identify endpoint ( g ).
> - How GPT-4V generates a reasonable route ( r ) from start ( s ) to endpoint ( g ).

Thanks for your suggestions. 

1. **Prompt SAM**: We have provided explanations in the caption of Figure 2, appendix B.2, . 
For enhanced clarification, prompt SAM is used to enhance event camera information by using YOLO's detection as prompts to eliminate noise. Additionally, it provides semantic segmentation masks for visual prompting, similar to the labelling technique in SOM[1], to assist visually grounded references in language descriptions.
For the first purpose as mentioned above, the mask from YOLO is used as the pixel prompts for SAM to rule out the area irrelated to the golf ball in the event camera. For the second purpose of providing  semantic segmentation, the SAM is applied with no prompts to generate a semantic segmentation mask of the entire image.

2. **RGB-D camera and event camera information composition**:   We have shown details in Lines 60-70, appendix B.1, and illustrated in Figure 2. To recap, 
* Camera calibriation and implementation: As detailed in Appendix B.1, line 92-94, we mentioned the mounting and calibration of the camera. To further elaborate, the event camera and the RGB-D camera are mounted in closed-distance and getting the top-down view of the court. The event camera provides a RGB stream along with event stream, we manually circles the four edges of the RGB image from bot event camera and the RGB-D camera. Then we perform perspective transformation to match the pixel space to the cartesian space. In this way the information from two cameras are matched to the same space.

* we first use YOLO to segment and then extract the position of golf ball from RGB-D information. The detected results are then used as prompts for SAM to segment the event camera frames, allowing us to isolate frames containing only the golf ball. This approach enables us to accurately determine the golf ball's position with high temporal resolution.


3. **Leveraging LISA to identify endpoint**: We have provided details in Line 122-124 and Appendix B.2.2.

- To recap and further explain the process, the user's input is processed using LLM to get a brief description of the desired goal. LISA then takes the textual input that describe the desired goal, along with the RGB image as reference. Based on these input, LISA will generate a mask that circles out the desired goal corresponding to the input textual description. To further clearly decide the exact goal, the mask from LISA is compared with the mask presented by SAM using Intersection over Union(IoU), and get the most matched item, to be presented in the following questions for GPT



4. **GPT-4V generation ways**: Details have been shown in line 126, line 100-103, caption of Figure 12, appendix F.2.
- To further elaborate, the process is constructed in a manner similar to SOM [1]. We provide an image of the RGB ground showing the directions of different obstacles and their possible paths. Next, we generate a pure prompt-based outline image alongside the RGB image. Then, an extensive and detailed prompt describing the task, target, and every object in the image is created. Using this information, GPT-4V will present an answer with the possible route toward the goal. We present an exact example demonstrating this process, please refer to the image


Sorry for the insufficient explanation on these details, we revised our paper to include the enhanced explanation above.

[1] Yang, Jianwei, et al. "Set-of-mark prompting unleashes extraordinary visual grounding in gpt-4v." arXiv preprint arXiv:2310.11441 (2023).



> **W4: Experimental Design:** 
> **- While the experiments demonstrate the framework's capabilities, there is a need for more structured and detailed experimental design, including control conditions and systematic variation of parameters to test different aspects of the framework.**
> **- Detailed reporting on the setup, execution, and outcomes of these experiments would strengthen the paper's contributions.**

We have already provided various experimental designs to test different aspects of RoboGolf.

As shown in the different levels of minigolf challenges we devised in our paper (see Figure 4), we consider a range of variations, including the positions, types, and combinations of obstacles and endpoints. These variations test spatial and kinodynamic understanding in various concrete ways, with analyses presented in Figure 4(b).

Thank you for your comments. We believe additional systematic parameters, such as lighting conditions to test perception capabilities and different grassland textures to test robustness, are intriguing directions for future work but are beyond the scope of our current study.



> **W5: Explanation of Training Processes:**
> **- The paper does not sufficiently explain the training processes for the policy models (e.g., Fv. Details on the training data, methodologies, and validation procedures are necessary for understanding how these models were developed and assessed.**
> **- Including information on the training regimen, hyperparameters, and evaluation metrics would provide a clearer picture of the model development process.**

Thank you for the suggestions. We have provided primary training process details for VLM, especially regarding the construction of the dataset, in Appendix B.2.

To further enhance clarity, we incorporate the following explanations into our revision:


"We specifically adopted LLAVA 1.5 as the fine-tuning backbone, refining it with our dataset. The validation of the model is integrated into the LLAVA training procedure, ensuring training effectiveness according to NLP standards. The training regimen consists of a single epoch with a batch size of 16 per device, utilizing the deepspeed library for acceleration. The learning rate is set to 2e-5, with no weight decay and a warmup ratio of 0.03. A cosine learning rate scheduler optimizes the training process over time. During training, although the model is not evaluated, the process is logged at every step, and the model is saved every 50,000 steps, retaining only the last checkpoint. The training is meticulously tracked and visualized using Weights & Biases, providing detailed insights into the model's performance. This comprehensive training regimen is designed to optimize the model's performance for the task while offering a transparent view of the training process."

Note that the capabilities of providing exact hitting parameters is strongly relying on the VLM's capabilities of using the tools for exact calculation, it will write and call python code to calculate the angle, estimate the length of the path and further provide the estimated parameters.




> **Q3: Detailed Methodological Explanations:**
> - Expand on the use of each component and how they integrate into the overall framework.
> - Ensure that all steps and processes are described clearly and concisely for better understanding.


We have provided explanations of the use of each component and how they integrate into the overall framework in various parts of our paper, such as the general overview in Figure 1, Lines 82-88, and throughout the Method section.

Per the reviewers' suggestions, we have further improved our paper for better understanding, as elaborated in our previous responses.

Finally, we hope we resolve all of your concerns and will continue to polish our language and the clarity in our revision. Thanks again for your comments and we wish you could reconsider your score.

