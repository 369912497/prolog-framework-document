Web API注解 - 注解pojo

为了在webapi中展示返回实体中字段的含义，需要在实体pojo中进行api的注解：

```
@Table(value = "t_product",columnPrefix="c_")
@ApiModel(description="产品实体")
public class Product implements Serializable{
    private static final long serialVersionUID = 1L;

    @Id
    @Column("c_id")
    @Identity
    @ApiModelProperty(value = "产品id")
    private int id;

    @Column("c_number")
    @ApiModelProperty(value = "产品编号")
    private String number;

    @Column("c_name")
    @ApiModelProperty(value = "产品名称")
    private String name;

    @ApiModelProperty(value = "产品价格")
    private float price;

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
    public float getPrice() {
        return price;
    }
    public void setPrice(float price) {
        this.price = price;
    }
}
```

> ##### @ApiModel\(description="产品实体"\)

##### 注解在类上，实体的说明

> ##### @ApiModelProperty\(value = "产品id"\)

注解在字段上，进行字段的释义

