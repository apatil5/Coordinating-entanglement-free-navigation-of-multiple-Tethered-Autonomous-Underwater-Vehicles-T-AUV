This work was done at IRSOL, Michigan Technological University which introduces heuristics to coordinate multiple Tethered-Autonomous Underwater Vehicles (T-AUVs), which can operate longer underwater due to continuous power and communication via the tether. The main challenge is preventing tether entanglement and collisions. The coordination problem involves three sub-problems:
1) task allocation (assigning tasks and determining the optimal sequence)
2) path planning (finding the best path for the given sequence)
3) scheduling (managing arrival and departure times to avoid collisions)

Solving these simultaneously for large problem size is complex and computationally demanding. Our initial research developed a primal-dual, multi-layer heuristic to address these challenges. To tackle this challenge, we considered the following min-max problem :
Given a set of T-AUVs with distinct depots and a set of tasks, find a path and schedule for each vehicle such that
1) each task must be handled by one of the vehicles
2) tethers are maintained untangled during the operation
3) the maximum travel time among all the vehicles is minimized (**Objective**)

In this approach, tasks are first distributed among the vehicles using a primal-dual-based heuristic that iteratively assigns tasks and generates a minimum spanning forest. The LKH algorithm is then applied to create cost-efficient paths for each vehicle. Assuming tethers remain taut and straight during movement between consecutive tasks, the paths are checked for potential tether entanglement or vehicle collisions. If entanglement is detected, the heuristic either reallocates tasks or adjusts vehicle schedules to avoid it. This process continues until all vehicle paths are entanglement-free. Refer the paper for detail: (https://www.mdpi.com/2339596)
In the video below, the four T-AUVs descent to their respecitive paths from their respective depots present on the top surface. The tethers remain straight during the operation, which is shown as the line joining the depot on the top surface and its respective vehicle. The video demonstrates cable entanglement detection with 4 T-AUVs (red, blue, green, violet) and 50 tasks, showing a potential entanglement between the red and blue cables at the end. 

https://github.com/user-attachments/assets/a806277b-82d7-483d-94cc-1bd5ca10d77a

After the reallocations and rescheduling, the resulting entanglement-free paths are shown below. These adjusted paths ensure that no tether entanglement or vehicle collisions occur, allowing the T-AUVs to perform their tasks efficiently and safely. You can see that the tasks have been reassigned from blue vehicle to other vehicles. You can also notice that the red robot yields for blue robot and waits for some time at task "b5" to avoid the entaglement. 

https://github.com/user-attachments/assets/e9ac806b-8fa7-4cc4-86cf-cd4251871e94

For a problem size of 3 T-AUVs and 50 tasks, the average and maximum computation times were 2.7 and 4.5 seconds, respectively. For larger problems with 10 T-AUVs and 100 tasks, the average and maximum times were 11.7 and 21.8 seconds. These computations were performed on an i7-7800X CPU (3.5 GHz) with 64 GB RAM, demonstrating the heuristic's computation efficiency and capability  of real-time coordination.

The initial multi-layer approach solved the problem by first allocating tasks and generating paths, then resolving entanglements. However, since it didn’t consider all constraints simultaneously, solution quality sometimes degraded during re-routing. To address this, a novel heuristic was developed with:

Modified Formulation:
1. A modified mixed integer linear program.
2. Entanglement constraints integrated into route planning.

New Heuristic:
1. Considers all constraints simultaneously.
2. Significantly improves solution quality.
3. Reduces computational costs compared to the multi-layer method.

The new heuristic is a local search-based approach that begins with a greedy task allocation to vehicles, ensuring no entanglements. It then reallocates tasks to balance the workload while maintaining entanglement-free operations. This approach optimizes task distribution and vehicle coordination. Further details are currently under embargo, as the paper is under peer review.

The video below shows entantanglement free paths for 3 T-AUVs and 100 tasks generated by the Primal Dual based multi layer heuristic.  Following the path and schedule, it can be noticed that the red vehicle has to wait for a long time to avoid entanglement. 

https://github.com/user-attachments/assets/ce2599c9-0058-4f60-8a23-935b1d66636e

The new heuristic results are shown below where the maximum travel time is reduced to 439 secs from 576 secs (red robot). The workload balance has also improved. 

https://github.com/user-attachments/assets/50cfaabe-9b02-4c3a-85f5-cfd0beedd864

Validated for 100 cases for each problem size, the new heuristic produces atleast 12% better solution than the solution produced by the primal dual based multi layer approach as shown in the below graph. The new heuriistic produces signficantly better solutions for larger problem sizes when compared with the Primal dual based multi layer heuristic.

![image](https://github.com/user-attachments/assets/27864a4f-fa38-4837-acac-cc7987a4aa5c)

Also the computation time for the larger problem size of 10 T-AUVs and 100 tasks is reduced by half and it has reduced multi fold for smaller problem sizes.

![image](https://github.com/user-attachments/assets/457102b4-a64e-4b98-b575-dba424de027a)

The new heuristic is flexible, easy to implement and computationally more efficient since it considers all the constraints simultaneously while allocating tasks and generating paths. In the future work, more realistic shapes of the tether will be considered considering the environment dynamics





