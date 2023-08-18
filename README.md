# Use Flat Lighting

global proc rf_toggleFlatLighting()
{
string $currentPanel = `getPanel -withFocus`;
if ( `modelEditor -q -dl $currentPanel` == "default") {
modelEditor -e -dl flat $currentPanel;
}
else {
modelEditor -e -dl "default" $currentPanel;
}
}

rf_toggleFlatLighting();

# WireFrameOnShded

string $selectedPanel = `getPanel -wf`;
int $shadedWireState = `modelEditor -q -wos $selectedPanel`;
if(`modelEditor -ex $selectedPanel`)
{
    setWireframeOnShadedOption (!$shadedWireState) $selectedPanel;
}

# Ao

if ( `getAttr "hardwareRenderingGlobals.ssaoEnable"` == 0 )
{
setAttr "hardwareRenderingGlobals.ssaoEnable" 1;
}
else
{
setAttr "hardwareRenderingGlobals.ssaoEnable" 0;
}
