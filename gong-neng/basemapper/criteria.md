## Criteria

框架中封装了Criteria类，主要用于查询条件的封装，其中包括对Restriction和Order的设置，使用方法如下示：

```
public List<OptionsVO> getByFatherId(String fatherId) {
		Criteria crt = Criteria.forClass(LmsTmsZone.class);
		Restriction rt=null;
		if(StringUtils.isEmpty(fatherId)){
			rt = Restrictions.eq("zlevel", 2);
		}else{
			rt = Restrictions.eq("fatherid", fatherId);
		}
		crt.setRestriction(rt);
		crt.setOrder(Order.asc(new String[]{"sortcode","zoneid"}));
		List<LmsTmsZone> list =  lmstmszoneMapper.findByCriteria(crt);
		
		return convertToOptions(list);
	}
```



