# test

getData(data, list) {
      switch (Object.prototype.toString.call(data)) {
        case '[object Array]':
          
          data.forEach((e, i) => {
            if(Object.prototype.toString.call(e) !== '[object Object]'){
                list.val = "["+data.toString()+"]"
                return false;
            }else{
               let children1 = []
                let obj1 = {
                  prop: i,
                  val: '',
                  children: children1
                }
                
                list.children.push(obj1)
                this.getData(e, obj1)
            }
           
          })
          break
        case '[object Object]':
          for (const key in data) {
            let children = []
            let obj = {
              prop: key,
              val: '',
              children: children
            }
            list.children.push(obj)
            this.getData(data[key], obj)
          }
          break
        default:
          list.val = data.toString()
      }
    },
