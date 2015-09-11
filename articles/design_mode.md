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
    
###总结
*   你要再加一个人类，只要你继续集成 Human 接口成了，然后啥都不用修改就可以生产了
*   延迟始化(Lazy initialization)，一个对象初始化完毕后就不释放，等到再次用到得就不用再次初始化了，直接从内存过中拿到就可以了

#抽象工厂模式
      定义一个人类接口
      public interface Human {
          public void laugh();
          public void cry();
          public void talk();
          public void sex();
      }
        
        定义一个黄种人
        public abstract class AbstractYellowHuman implements Human {
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
        女性黄种人
        public class YellowFemaleHuman extends AbstractYellowHuman {
            public void sex() {
                System.out.println("该黄种人的性别为女...");
            }
        }
        男性黄种人
        public class YellowMaleHuman extends AbstractYellowHuman {
            public void sex() {
                System.out.println("该黄种人的性别为男....");
            }
        }
        
        接口工厂
        public interface HumanFactory {
            //制造黄色人类
            public Human createYellowHuman();
            //制造一个白色人类
            public Human createWhiteHuman();
            //制造一个黑色人类
            public Human createBlackHuman();
        }
        
        抽象类工厂
        public abstract class AbstractHumanFactory implements HumanFactory {
            protected Human createHuman(Class c) {
                Human human = null;
                try {
                    //直接产生一个实例
                    human = (Human)Class.forName(c.getName()).newInstance();
                } catch (Exception e) {
                    e.printStackTrace();
                }
                return human;
            }
        }
        
        男性创建工厂
        public class MaleHumanFactory extends AbstractHumanFactory {
            //创建一个男性黑种人
            public Human createBlackHuman() {
                return super.createHuman(BlackMaleHuman.class);
            }
            //创建一个男性白种人
            public Human createWhiteHuman() {
                return super.createHuman(WhiteMaleHuman.class);
            }
            //创建一个男性黄种人
            public Human createYellowHuman() {
                return super.createHuman(YelloMaleHuman.class);
            }
        }
        public class NvWa {
            public static void main(String[] args) {
                //第一条生产线，男性生产线
                HumanFactory maleHumanFactory = new MaleHumanFactory();
                //第二条生产线，女性生产线
                HumanFactory femaleHumanFactory = new FemaleHumanFactory();
                //生产线建立完毕，开始生产人了:
                Human maleYellowHuman = maleHumanFactory.createYellowHuman();
                Human femaleYellowHuman = femaleHumanFactory.createYellowHuman();
                maleYellowHuman.cry();
                maleYellowHuman.laugh();
                femaleYellowHuman.sex();
            }
        }
###总结
*   如果存在双性人，那么只要继承两个抽象类AbstractHumanFactory，AbstractYellowHuman，分别增加人和工厂就可以了
*   高内聚，低耦合
