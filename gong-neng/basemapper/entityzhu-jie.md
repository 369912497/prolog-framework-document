## Entity注解

Entity注解主要是为BaseMapper服务，用于描述实体与数据表之间的对应关系

示例：

```
@Table(columnPrefix="c_",value="cyctest")
public class User {
    @Id
    private int id;
    @AutoKey(dialect=AutoKey.DIALECT_ORACLE,type=AutoKey.TYPE_SEQUENCE,sequence="plg_test_sequence")
    private String number;
    private String name;

    @One(property="zoneid")
    @Column("c_zoneid")
    private LmsTmsZone zone;


    @One(property="zoneid")
    @Column("c_zoneid2")
    private LmsTmsZone zone2;

    @Ignore
    private int status;


    public int getStatus() {
        return status;
    }
    public void setStatus(int status) {
        this.status = status;
    }
    public LmsTmsZone getZone2() {
        return zone2;
    }
    public void setZone2(LmsTmsZone zone2) {
        this.zone2 = zone2;
    }
    public int getId() {
        return id;
    }
    public void setId(int id) {
        this.id = id;
    }
    public String getNumber() {
        return number;
    }
    public void setNumber(String number) {
        this.number = number;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public LmsTmsZone getZone() {
        return zone;
    }
    public void setZone(LmsTmsZone zone) {
        this.zone = zone;
    }
}
```



