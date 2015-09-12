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

#单例模式

*   类在内存中只能有一个对象
*   外界不能够随意创建对象，把构造方法私有
*   类本身要创建一个对象
*   通过公共的方式提供给别人

###饿汉式
        class Single{
        	private static final Single s = new Single();
        	private Single(){}
        	public static Single getInstance(){
        		return s;
        	}
        }

###懒汉式
        class Single {
        	private static Single s = null;
        	private Single(){}
        	public static  Single getInstance(){
        		if(s==null){
        			synchronized(Single.class){
        				if(s==null)
        					s = new Single();
        			}
        		}
        		return s;
        	}
        }

#适配器模式
笔记本电源线上的黑盒子就是个适配器，一般你在中国能用，在日本也能用，虽然两个国家的的电源电压不同，中国是 220V，日本是110V，但是这个适配器能够把这些不同的电压转换为你需要的 36V 电压，保证你的笔记本能够正常运行

        公司内部员工用户信息对象
        public interface IUserInfo {
            //获得用户姓名
            public String getUserName();
            //获得家庭地址
            public String getHomeAddress();
            //手机号码
            public String getMobileNumber();
            //办公电话，一般式座机
            public String getOfficeTelNumber();
            //这个人的职位是啥
            public String getJobPosition();
            //获得家庭电话
            public String getHomeTelNumber();
        }
        
        接口的实现类
        public class UserInfo implements IUserInfo {
            public String getHomeAddress() {
                System.out.println("这里是员工的家庭地址....");
                return null;
            }
            public String getHomeTelNumber() {
                System.out.println("员工的家庭电话是....");
                return null;
            }
            public String getJobPosition() {
                System.out.println("这个人的职位是BOSS....");
                return null;
            }
            public String getMobileNumber() {
                System.out.println("这个人的手机号码是0000....");
                return null;
            }
            public String getOfficeTelNumber() {
                System.out.println("办公室电话是....");
                return null;
            }
            public String getUserName() {
                System.out.println("姓名叫做...");
                return null;
            }
        }
        
        使用
        public class App {
            public static void main(String[] args) {
                IUserInfo youngGirl = new UserInfo();
                //调用方法即可
                ......(自己的代码)
            }
        }
        
        公司外部员工信息
        public interface IOuterUser {
            //基本信息，比如名称，性别，手机号码了等
            public Map getUserBaseInfo();
            //工作区域信息
            public Map getUserOfficeInfo();
            //用户的家庭信息
            public Map getUserHomeInfo();
        }
        实现类
        public class OuterUser implements IOuterUser {
            public Map getUserBaseInfo() {
                HashMap baseInfoMap = new HashMap();
                baseInfoMap.put("userName", "这个员工叫混世魔王....");
                baseInfoMap.put("mobileNumber", "这个员工电话是....");
                return baseInfoMap;
            }
            public Map getUserHomeInfo() {
                HashMap homeInfo = new HashMap();
                homeInfo.put("homeTelNumbner", "员工的家庭电话是....");
                homeInfo.put("homeAddress", "员工的家庭地址是....");
                return homeInfo;
            }
            public Map getUserOfficeInfo() {
                HashMap officeInfo = new HashMap();
                officeInfo.put("jobPosition","这个人的职位是BOSS...");
                officeInfo.put("officeTelNumber", "员工的办公电话是....");
                return officeInfo;
            }
        }
        
        将外部员工信息导入公司内部
        public class OuterUserInfo extends OuterUser implements IUserInfo {
            private Map baseInfo = super.getUserBaseInfo(); //员工的基本信息
            private Map homeInfo = super.getUserHomeInfo(); //员工的家庭 信息
            private Map officeInfo = super.getUserOfficeInfo(); //工作信息
            public String getHomeAddress() {
                String homeAddress = (String)this.homeInfo.get("homeAddress");
                System.out.println(homeAddress);
                return homeAddress;
            }
            public String getHomeTelNumber() {
                String homeTelNumber = (String)this.homeInfo.get("homeTelNumber");
                System.out.println(homeTelNumber);
                return homeTelNumber;
            }
            public String getJobPosition() {
                String jobPosition = (String)this.officeInfo.get("jobPosition");
                System.out.println(jobPosition);
                return jobPosition;
            }
            public String getMobileNumber() {
                String mobileNumber = (String)this.baseInfo.get("mobileNumber");
                System.out.println(mobileNumber);
                return mobileNumber;
            }
            public String getOfficeTelNumber() {
                String officeTelNumber = (String)this.officeInfo.get("officeTelNumber");
                System.out.println(officeTelNumber);
                return officeTelNumber;
            }
            public String getUserName() {
                String userName = (String)this.baseInfo.get("userName");
                System.out.println(userName);
                return userName;
            }
        }
