#工厂方法模式

    定义一个人类接口
    public interface Human {
      public void laugh();
      public void cry();
      public void talk();
    }
    
    定义黄种人
    public class YellowHuman implements Human {
      public void cry() {
        System.out.println("黄色人类会哭");
      }
      public void laugh() {
        System.out.println("黄色人类会大笑，幸福呀！");
      }
      public void talk() {
        System.out.println("黄色人类会说话，一般说的都是双字节");
      }
    }
    
    定义白种人
    public class WhiteHuman implements Human {
      public void cry() {
        System.out.println("白色人类会哭");
      }
      public void laugh() {
        System.out.println("白色人类会大笑，侵略的笑声");
      }
      public void talk() {
        System.out.println("白色人类会说话，一般都是但是单字节！");
      }
    }
    
    定义黑种人
    public class BlackHuman implements Human {
      public void cry() {
        System.out.println("黑人会哭");
     }
     public void laugh() {
       System.out.println("黑人会笑");
      }
     public void talk() {
        System.out.println("黑人可以说话，一般人听不懂");
     }
    }
    
    定义工厂
    public class HumanFactory {
      // 定义一个 MAP, 初始化过的 Human 对象都放在这里
      private static HashMap<String,Human> humans = new HashMap<String,Human>();
      public static Human createHuman(Class c){
        Human human=null; // 定义一个类型的人类
        try {
          if(humans.containsKey(c.getSimpleName())){
          human = humans.get(c.getSimpleName());
        }else{
          human = (Human)Class.forName(c.getName()).newInstance();
          // 放到 MAP 中
          humans.put(c.getSimpleName(), human);
        } 
      } catch (Exception e) {
        System.out.println(" 工厂创建失败 ");
      } 
      return human;
      }
    }
    
    使用
    public class NvWa {
      public static void main(String[] args) {
        Human yellowHuman = HumanFactory.createHuman(YellowHuman.class);
        yellowHuman.cry();
        yellowHuman.laugh();
        yellowHuman.talk();
      }
    }
