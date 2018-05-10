## @AutoKey

> ##### 说明

@AutoKey用于定义字段自动填充策略，注解在字段上

> ##### 源码

```

@Retention(RetentionPolicy.RUNTIME)
@Documented
@Target(ElementType.FIELD)
public @interface AutoKey {
	
	public static final short TYPE_IDENTITY=0;
	public static final short TYPE_SEQUENCE=1;
	public static final short TYPE_UUID=2;
	
	
	public static final short DIALECT_ORACLE = 0;
	public static final short DIALECT_DB2 = 1;
	public static final short DIALECT_H2 = 2;
	public static final short DIALECT_POSTGRE = 3;
	
	/**
	 * 
	 *填充值策略
	 *
	 * @Title: type   
	 * @return short      
	 * @date 2018年5月9日 上午11:54:25
	 */
	short type();
	
	/**
	 * 
	 *数据库类型
	 *
	 * @Title: dialect   
	 * @return short      
	 * @date 2018年5月9日 上午11:54:41
	 */
	short dialect() default 0;
	
	/**
	 * 
	 *sequence名称
	 *
	 * @Title: sequence   
	 * @return String      
	 * @date 2018年5月9日 上午11:54:55
	 */
	String sequence() default "plg_fx_sequence";
}

```



