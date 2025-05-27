EMS

state
- pv output
- dynamic price
- state of charge
- load profile

action:
- BESS
- additional main grid power exchange

reward:
- min cost + max util + soc scope

---

FCS, don't consider the bess and renewable

state
- start time
- end time
- state of charge in electric vehicle
  
action:
- charging/discharging power of charging pale in station, assuming that you can fully control every pale corresponding with every car.
- vehicle to grid, v2g action, only for a part of vehicles which selected this charging mode, and has a upper bound.

reward:
- min load fluctuation + min waiting time + delay penalty












---
Some Ideas:

LaTeX for pdf? 这么标致好看适合打印，why not LaTeX for HTML


