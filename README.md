# HEPSPLC
HEPS PLC code
# 2022.03.10
加入谱学扫描功能
#
# 2022.04.19
谱学扫描功能完成
#
# 2022.04.20#
添加了安全限位数据的获取，以及HMI显示
#
# 2022.04.20
1.加入在无光栅下设置gap位置
2.加入输入保护
3.加入Error和描述，重新梳理了ErrorId
#
# 2022.04.26
1.recipe加入参数表修改后PLC自动加载参数
2.加入光栅positionBias PLC程序和配方
3.emergencyStop加入HMI
#
# 2022.04.28
 1.taper模式下代码更改，补偿方式由简单地1/2Taper，到右轴由补偿表解算
 2.更改了位置和速度的Threshold，并更新了配方
#
# 2022.05.05
 1.更新了Possdiff程序的漏洞
 2.加入光栅位置监控保护
#
#
#2022.05.27 配方中加入USELinearEncoeder
//如果没有光栅，则不判断四轴位置
IF NOT USELinearEncoeder THEN
	RETURN;
END_IF
#
# 2022.06.04
Ver.25
add dicimal cut to 5
位置速度等小数位数在PLC程序中减少为5位
#
# 2022.06.20
Ver.26 modified bug on Hysteresis Mode
·修改了程序BUG：磁间隙先打开，后拉近时，不能回城走的问题
·问题原因是在拉开磁间隙时，m_State不能回到0，这一问题是由于targetPosLessThanCurrentPos在磁间隙到位后立即变化
·修改方法为：targetPosLessThanCurrentPos判断方向，只在m_State=0 AND n_State=0的时候做
#
# 2022.07.11
Ver.27 add temperature reading from lakeshore
#