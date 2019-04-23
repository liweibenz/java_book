# 文件操作

### 1. 获取目录下文件的数量
```java
  public static int getFileCount(String path){
        int num = 0;
        File file = new File(path);
        if (file.exists()){
            File[] f = file.listFiles();
            for (File file1 : f) {
                if (file1.isFile()){
                    num++;
                    //System.out.println(num+":"+file1.getName());

                }
            }
        }

        return num;
    }


    public static void main(String[] args) {

        System.out.println(getFileCount("/Users/liwei/Downloads"));
        
    }
```    

