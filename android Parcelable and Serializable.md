#为什么要使用序列化
    1.永久性保存对象，保存对象的属性到本地文件、数据库中方便数据传输，；
    2.对象在网络中传递；
    3.对象在IPC间传递。
#序列化方法
    在Android系统中关于序列化的方法一般有两种，分别是实现Serializable接口和Parcelable接口,
    其中Serializable接口是来自Java中的序列化接口，而Parcelable是Android自带的序列化接口。
#各自优缺点
    Serializable：
      谨慎的实现Serializable接口
      1.一旦一个类被发布，就大大降低了“改变这个类的实现”的灵活性
      2.增加了出现Bug和安全漏洞的可能性
      3.随着类发行新的版本，相关的测试负担增加
      4.Serializable在序列化的时候会产生大量的临时变量，从而引起频繁的GC
      优点：需要持久化保存对象时选择Serializable
      可以考虑用序列化代理代替序列化实例
      
      Parcelable：
      Parcelable的设计初衷是因为Serializable效率过慢
      Parcelable的性能比Serializable好，在内存开销方面较小，所以在内存间数据传输时（activity间传输数据，序列化对象在网络中传递对象或序列化在进程间传递对象）推荐使用Parcelable。
      缺点：因为android不同版本Parcelable可能不同，所以不推荐使用Parcelable进行数据持久化
#使用
    1.Serializable的接口实现很简单，只需让需要序列化的类继承Serializable 即可，系统会自动将其序列化

    2.实现Parcelable接口主要可以分为一下几步：
    1）implements Parcelable。
    2）重写writeToParcel方法，将你的对象序列化为一个Parcel对象，即：将类的数据写入外部提供的Parcel中，打包需要传递的数据到Parcel容器保存，以便从Parcel容器获取数据。
    3）重写describeContents方法，内容接口描述，默认返回0即可。
    4）实例化静态内部对象CREATOR实现接口Parcelable.Creator 。
    注意:若将Parcel看成是一个流，则先通过writeToParcel把对象写到流里面，再通过createFromParcel从流里读取对象，因此类实现的写入顺序和读出顺序必须一致。 
    
      public class Person implements Parcelable {
        private String mName;
        private String mSex;
        private int mAge;
 
      public String getmName() {
       return mName;
      }
 
      public void setmName(String mName) {
       this.mName = mName;
      }
 
      public String getmSex() {
        return mSex;
      }
 
      public void setmSex(String mSex) {
        this.mSex = mSex;
      }
 
      public int getmAge() {
       return mAge;
      }
 
      public void setmAge(int mAge) {
       this.mAge = mAge;
      }
 
      @Override
      public int describeContents() {
        return 0;
      }
 
      @Override
      public void writeToParcel(Parcel dest, int flags) {
        dest.writeString(mName);
        dest.writeString(mSex);
        dest.writeInt(mAge);
      }
 
      public static final Parcelable.Creator<Person> CREATOR = new Creator<Person>() {
 
     @Override
    public Person createFromParcel(Parcel source) {
      Person person = new Person();
      person.mName = source.readString();
      person.mSex = source.readString();
      person.mAge = source.readInt();
      return person;
    }
 
    //供反序列化本类数组时调用的
    @Override
    public Person[] newArray(int size) {
      return new Person[size];
    }
     };
