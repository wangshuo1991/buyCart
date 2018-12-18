# buyCart -- 购物车
基于vue和axios实现的简单的购物车列表：主要功能有全选和反选（checkbox），商品删除（deleteItem），以及计算商品数量总和(count)和商品总价格(totalPrice)。

### 实现反选和全选 - computed 计算属性实现

```javascript
checkAll: {  
           get(){  
                 return this.dataAry.every(item=>item.isSelected);
           },
           set(val){   // 实现全选和反选的set
                 this.dataAry.forEach(item=>item.isSelected=val);
           }
         }
```


### 实现价格和 （实现商品数量综合亦是同样的方法）

```javascript
sum () { // 数组reduce方法实现累加计算价格
                    return this.dataAry.reduce((prev,next)=>{
                        if(!next.isSelected) return prev;
                        return prev+next.productPrice*next.productCount;
                    },0)
                }
```

### 实现删除列表中的某一项

```javascript
deleteItem(item){ // 过滤出这一项即可
                    this.dataAry = this.dataAry.filter(ele=>ele!=item);
                }
```

还可以用index为参数 - 就是列表的索引值的方法删除。

```javascript
deleteItem(index){ // 过滤出这一项即可
                    this.dataAry .splice(index,1);
                }
```
