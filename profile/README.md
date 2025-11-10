# Automated Solar Panel Fault Detection and Maintenance System

## Demo SOP/checklist
- TODO: are we flying a drone?? if so, add drone cage procedure

### Demo preparation
- [ ] Layout
  - [ ] Determine [frame of reference and coordinate system](#coordinates)
  - [ ] Mark panel locations according to the [demo layout](#demo-layout)
  - [ ] Mark AruCo marker locations according to the [demo layout](#demo-layout)
  - [ ] Mark initial drone and rover positions according to the [demo layout](#demo-layout)
- [ ] Batteries
  - [ ] Drone battery fully charged
  - [ ] Rover motor battery (Li-poly) fully charged
  - [ ] Rover power bank fully charged
  - [ ] Backend laptop/desktop fully charged
    - [ ] Laptop charger is present
  - [ ] Frontend laptop/dekstop fully charged
    - [ ] Laptop charger is present
- [ ] Configuration
  - [ ] Jetson automatically starts `JETNET_AP` hotspot when turned on
  - [ ] Drone automatically connects to `jetnet` network
- [ ] Video
  - [ ] Video present on both laptops (frontend/backend)
  - [ ] Video present on USB drive
  - [ ] Video present on Google Drive
  - [ ] TV or large monitor present in demo room

### Before demo
- [ ] Prepare video for display on monitor
- [ ] Place drone, rover, panels, AruCo markers on layout markers
- [ ] Plug in rover power (Li-poly to wheels)
- [ ] Plug in Jetson power (power bank to Jetson)
  - Use the 65W USB-C output on the power bank and the USB-C input above the barrel jack on the Jetson.
- [ ] Connect backend laptop to `jetnet` network
- [ ] Initialize Docker cluster on backend laptop
  - [ ] Ensure backend is serving API to `10.42.0.111:4181`
      - TODO: is this IP right?
    - Test with `curl 10.42.0.111:4181/api/panels` or similar
- [ ] Connect frontend laptop to `jetnet` network
- [ ] Confirm drone presence on network
  - TODO: what's the Clover site address?
- [ ] Initialize ROS nodes on rover
  - TODO: finalize, write commands
- [ ] Initialize ROS nodes on drone
  - TODO: finalize, write commands

### During demo
- TODO: describe when/how SLM is used
- [ ] Send chat to SLM requesting panel review
- [ ] Drone takes off and flies to panel cluster
- [ ] Drone takes picture of panels and sends to Jetson
- [ ] Drone flies to starting point and lands
- [ ] Jetson reviews picture
- [ ] Jetson notices defect (`snow`) on panel 1
- [ ] Jetson creates panel update and posts to backend
- [ ] Backend notes dirty panel and sends rover
- [ ] Backend updates database (visible on frontend)
- [ ] Refresh frontend to show change in panel status (as rover is moving?)
- [ ] Rover navigates to affected panel
- [ ] Rover blows paper off affected panel
- [ ] Jetson indicates completed operation to backend
- [ ] Backend updates database, SLM
- [ ] Rover returns to starting point
- [ ] Refresh frontend to show change (in rover position)

### After demo & teardown
- TODO: confirm order
- [ ] Ensure drone is grounded and disarmed
- [ ] Disconnect rover motors (break XT60 connection to Li-poly)
- [ ] Shut drone down remotely (`ssh` in then `sudo shutdown now`)
- [ ] Shut down SLM/frontend
- [ ] Shut down Docker backend cluster
- [ ] Shut Jetson down remotely (`ssh` in then `sudo shutdown now`)
- [ ] Disconnect Jetson from power (remove USB-C to power bank)
- [ ] Remove panels, AruCo markers
- [ ] Remove and store drone and rover
- [ ] Remove layout markers

### Demo Layout

#### Physical
- TODO: fill out marker locations
- TODO: fill out metric conversions
- `+x` is the direction from the rover start to the panel cluster, and is "forward" in the demo.
- `+y` is orthogonal to `+x` and points to the right (looking along `+x`).
| Name        | `x` (in)            | `y` (in)            | `x` (m)             | `y` (m)             |
| ---         | ---                 | ---                 | ---                 | ---                 |
| Panel 1     | +80                 | -20                 |                     |                     |
| Panel 2     | +80                 | +20                 |                     |                     |
| Panel 3     | +40                 | -20                 |                     |                     |
| Panel 4     | +40                 | +20                 |                     |                     |
| Marker 1    |                     |                     |                     |                     |
| Marker 2    |                     |                     |                     |                     |
| Marker 3    |                     |                     |                     |                     |
| Marker 4    |                     |                     |                     |                     |
| Marker 5    |                     |                     |                     |                     |
| Drone start | 0                   | +40                 |                     |                     |
| Rover start | 0                   | 0                   | 0                   | 0                   |

#### Network
- TODO: fill out `jetnet` last quartets
| Name            | `jetnet` IPv4 |
| ---             | ---           |
| Jetson          | 10.42.0.1     |
| Drone Pi        | 10.42.0.*     | 
| Backend laptop  | 10.42.0.*     |
| Frontend laptop | 10.42.0.*     |
