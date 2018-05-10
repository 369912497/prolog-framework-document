## Page

Page是对分页对象进行了封装（com.prolog.framework.core.pojo.Page）,通常在分页查询中使用：

```
@Override
    public Page<LmsTmsZone> getByCriteriaForPage(Criteria criteria, int pageNum, int pageSize) {
        // TODO Auto-generated method stub
        PageHelper.startPage(pageNum, pageSize);
        Page<LmsTmsZone> page = PageUtils.getPage(lmstmszoneMapper.findByCriteria(criteria));
        return page;
    }
```



