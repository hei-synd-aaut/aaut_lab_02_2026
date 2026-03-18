<h1 align="left">
  <br>
  <img src="../img/hei-en.png" alt="HEI-Vs Logo" width="350">
  <br> Advanced Automation Lab 02
  <br>
</h1>

Author: [Cédric Lenoir](mailto:cedric.lenoir@hevs.ch)


# Exercice suggéré.

## Ajouter un EM_Vision

S'inspirer de EM_Exemple.

1.  Hériter de EM_Abstract
2.  Instantier
3.  Appeler
4.  Ajouter dans whatSC

## Ajouter dans EM_Vision

```iecst
VAR
  xCameraOn         : BOOL; // Condition for resetting
  xCameraOff        : BOOL; // Condition for Stopping
  xCalibrateCamera  : BOOL; // Some time in starting
  tonCalibrate      : TON;  // About T#10s
END_VAR
```

### Add states for

1.  resetting / wait xCameraOn, reset xCameraOff and xCalibrateCamera
2.  stopping  / wait xCameraOff then reset other flags
3.  starting  / wait timer tonCalibrate

### Add warning

in resetting, stopping and starting if time in state > 5s

### Add alarm stop

If state execute and xCameraOff, alarm stop.


## Interface

Add EM_Vision in arrayOfI_Module to display if EM is SC or not.


## Add Command parameter

Add in parameters of PackTag

```iecst
// Timer parameter for calibration with type converion.
// Rem if DINT 1 is 1ms
// Set xCameraOn
// Set xCameraOff
// Use on of these tags
    PackTag.Command.Parameter_Lreal[5].ID := 2005;
    PackTag.Command.Parameter_Lreal[5].Name := 'User define 1';
    PackTag.Command.Parameter_Lreal[5].Unit := '--';
    
    PackTag.Command.Parameter_Lreal[6].ID := 2006;
    PackTag.Command.Parameter_Lreal[6].Name := 'User define 2';
    PackTag.Command.Parameter_Lreal[6].Unit := '--';
    
    PackTag.Command.Parameter_Lreal[7].ID := 2007;
    PackTag.Command.Parameter_Lreal[7].Name := 'User define 3';
    PackTag.Command.Parameter_Lreal[7].Unit := '--';
    
    PackTag.Command.Parameter_Lreal[8].ID := 2008;
    PackTag.Command.Parameter_Lreal[8].Name := 'User define 4';
    PackTag.Command.Parameter_Lreal[8].Unit := '--';
    
    PackTag.Command.Parameter_Lreal[9].ID := 2009;
    PackTag.Command.Parameter_Lreal[9].Name := 'User define 5';
```


<!-- End of file -->