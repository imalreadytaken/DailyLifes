##SQL
- 默认值

  - IFNULL(field,0) as field
- 类型转换
	- CAST(SUM(pv_exp) AS UNSIGNED) as pv_exp
	- 类型有：			

			BINARY[(N)]
		​	CHAR[(N)]
		​	DATE
		​	DATETIME
		​	DECIMAL[(M[,D])]
		​	SIGNED [INTEGER]
		​	TIME
		​	UNSIGNED [INTEGER]

	- 直接做+操作可以转为数值型

			IFNULL(ROUND(pv_click / pv_exp * 100,2) + "", 0)
- 四舍五入

  - ROUND(number，要保留的小数位)

- 添加partition
  - alter table tb_name add partition (partition part_name values ( =| less than | ... )  (xxx) )

