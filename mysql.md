# Mysql
```mysql
SELECT u.nickname,u.phone,u.power_lv, CASE o.team_lv2_id WHEN 0 THEN o.team_lv1_id ELSE o.team_lv2_id END AS team_id, COUNT(*) AS COUNT
FROM gy_order o
INNER JOIN gy_user u ON u.id = CASE o.team_lv2_id WHEN 0 THEN o.team_lv1_id ELSE o.team_lv2_id END
WHERE o.activity_id = 301
where o.status > 0
GROUP BY team_id
ORDER BY COUNT DESC
LIMIT 10


SELECT u.nickname,u.phone,u.power_lv, CASE o.team_lv2_id WHEN 0 THEN 0 ELSE o.team_lv1_id END AS saler_id, COUNT(*) AS COUNT
FROM gy_order o
INNER JOIN gy_user u ON u.id = CASE o.team_lv2_id WHEN 0 THEN 0 ELSE o.team_lv1_id END
WHERE o.activity_id = 301
where o.status > 0
GROUP BY saler_id
ORDER BY COUNT DESC
LIMIT 30
```

### mysql在Linux下安装
[传送门]("https://blog.csdn.net/weixin_52850476/article/details/122800696")