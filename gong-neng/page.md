## Page

Page是对分页对象进行了封装（com.prolog.framework.core.pojo.Page）,通常在分页查询中使用：

```java
@Override
    public Page<LmsTmsZone> getByCriteriaForPage(Criteria criteria, int pageNum, int pageSize) {
        // TODO Auto-generated method stub
        PageHelper.startPage(pageNum, pageSize);
        Page<LmsTmsZone> page = PageUtils.getPage(lmstmszoneMapper.findByCriteria(criteria));
        return page;
    }
```

源码：

```
public class Page<T> implements Serializable{

    private static final long serialVersionUID = 1L;

    @ApiModelProperty("数据列表")
    private List<T> list;

    @ApiModelProperty("总记录数")
    private long totalCount;

    @ApiModelProperty("总页数")
    private int pageCount;

    @ApiModelProperty("当前页码")
    private int pageNum;

    @ApiModelProperty("每页大小")
    private int pageSize;

    @ApiModelProperty("当前页开始行")
    private int startRow;

    @ApiModelProperty("当前页结束行")
    private int endRow;


    public int getStartRow() {
        return startRow;
    }

    public void setStartRow(int startRow) {
        this.startRow = startRow;
    }

    public int getEndRow() {
        return endRow;
    }

    public void setEndRow(int endRow) {
        this.endRow = endRow;
    }

    public List<T> getList() {
        return list;
    }

    public void setList(List<T> list) {
        this.list = list;
    }

    public long getTotalCount() {
        return totalCount;
    }

    public void setTotalCount(long totalCount) {
        this.totalCount = totalCount;
    }

    public int getPageCount() {
        return pageCount;
    }

    public void setPageCount(int pageCount) {
        this.pageCount = pageCount;
    }

    public int getPageNum() {
        return pageNum;
    }

    public void setPageNum(int pageNum) {
        this.pageNum = pageNum;
    }

    public int getPageSize() {
        return pageSize;
    }

    public void setPageSize(int pageSize) {
        this.pageSize = pageSize;
    }


}
```



