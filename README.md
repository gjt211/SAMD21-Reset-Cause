# SAMD21-Reset-Cause
Detecting the reset cause in Arduino on SAMD21 based boards

I was looking for a way to determine what was the cause of reset on my MKRZero board and without any success the following is what I determined.

You can access a register in Arduino named `REG_PM_RCAUSE` and you can test it against several values to determine the reset cause.

Example:
```
if (REG_PM_CAUSE == PM_RCAUSE_SYST){
  Serial.println("Reset requested by system");
}
if (REG_PM_CAUSE == PM_RCAUSE_WDT){
  Serial.println("Reset requested by Watchdog");
}
if (REG_PM_CAUSE == PM_RCAUSE_EXT){
  Serial.println("External reset requested");
}
if (REG_PM_CAUSE == PM_RCAUSE_BOD33){
  Serial.println("Reset brown out 3.3V");
}
if (REG_PM_CAUSE == PM_RCAUSE_BOD12){
  Serial.println("Reset brown out 1.2v");
}
if (REG_PM_CAUSE == PM_RCAUSE_POR){
  Serial.println("Normal power on reset");
}
```
