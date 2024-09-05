This work was done at IRSOL, MTU which introduces heuristics to coordinate multiple Tethered-Autonomous Underwater Vehicles (T-AUVs), which can operate longer underwater due to continuous power and communication via the tether. The main challenge is preventing tether entanglement and collisions. The coordination problem involves three sub-problems:
1) task allocation (assigning tasks and determining the optimal sequence),
2) path planning (finding the best path for the given sequence), 
3) scheduling (managing arrival and departure times to avoid collisions).

Solving these simultaneously for large problem size is complex and computationally demanding. Our initial research developed a primal-dual, multi-layer heuristic to address these challenges. In this approach, tasks are first distributed among the vehicles using a primal-dual-based heuristic that iteratively assigns tasks and generates a minimum spanning forest. The LKH algorithm is then applied to create cost-efficient paths for each vehicle. Assuming tethers remain taut and straight during movement between consecutive tasks, the paths are checked for potential tether entanglement or vehicle collisions. If entanglement is detected, the heuristic either reallocates tasks or adjusts vehicle schedules to avoid it. This process continues until all vehicle paths are entanglement-free. The video demonstrates cable entanglement detection with 3 T-AUVs and 50 tasks, showing a potential entanglement between the red and blue cables at the end.

https://github.com/user-attachments/assets/a806277b-82d7-483d-94cc-1bd5ca10d77a

After 


https://github.com/user-attachments/assets/e9ac806b-8fa7-4cc4-86cf-cd4251871e94

Building on that, we propose an iterative heuristic that allocates tasks while proactively preventing entanglements. Simulations with varying problem sizes show the algorithm's effectiveness and real-time potential, offering reliable solutions efficiently. This research advances underwater robotics with practical applications for T-AUV systems.




https://github.com/user-attachments/assets/f438e7ef-3b3d-4325-9a35-09347dc0d833


new primal dual

https://github.com/user-attachments/assets/ce2599c9-0058-4f60-8a23-935b1d66636e

Novel approach



https://github.com/user-attachments/assets/50cfaabe-9b02-4c3a-85f5-cfd0beedd864







