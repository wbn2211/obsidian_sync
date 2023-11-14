tag:
#游戏/CSGO/游戏设置/kzbhop 

---

```CSGO
//允许作弊

sv_cheats 1;

//开局冻结时间

mp_freezetime 0;

//存点

bind "mouse4" "exec tppos.log; noclip";

//读点

bind "mouse5" "con_logfile cfg/tppos.log; getpos_exact; con_logfile 0;say 存点成功";

//跳跃体力惩罚

sv_staminajumpcost 0;

//跳跃落地体力惩罚

sv_staminalandcost 0;

//体力惩罚最大值

sv_staminamax 0;

//体力惩罚恢复

sv_staminarecoveryrate 0;

//

sv_ladder_scale_speed 1;

//

sv_clamp_unsafe_velocities;

//

cl_showpos 1;

//空中加速度

sv_airaccelerate 1000;

//允许连跳

sv_enablebunnyhopping 1;

//自动连跳

sv_autobunnyhopping 1;

//隐蔽HUD、准星、击杀显示

//cl_drawhud 0;

//无敌

gods;

//关闭实时显示投掷物轨迹

cl_grenadepreview 0;

//关闭显示投掷物轨迹

sv_grenade_trajectory 0;

//踢出bot

bot_kick;

//回复生命

sv_regeneration_force_on 1;

//掉落伤害

sv_falldamage_scale 0;

//CT死后复活

mp_respawn_on_death_ct 1;

//T死后复活

mp_respawn_on_death_t 1;

//CT复活时间

mp_respawnwavetime_ct 2;

//T复活时间

mp_respawnwavetime_t 2;

//关闭胜负条件

mp_ignore_round_win_conditions 1;

//1s后重启游戏

mp_restartgame 1;
```