# zer.exec :wrench:
#### A small module for executing external programs.

## Do you want to run some program? :rocket:

<details>
  <summary>Main.java</summary>
  
  ```java
  import zer.exec.EXECTask;
  import zer.exec.EXECResult;
  import zer.exec.EXECResultCode;

  public class Main
  {
    public static void main(String[] args)
    {
      EXECResult res = EXECTask.exec("echo Hello, world!");
      if (res.code() != EXECResultCode.OK)
      {
        System.out.println("[error]: " + res.message());
        return;
      }

      System.out.println(res.message());
    }
  }
  ```
</details>

<details>
  <summary>Result</summary>
  
  ```
  $ javac Main.java
  $ java Main
  Hello, world!
  ```
</details>

## Or maybe you want to run some program with a timeout? :clock9:

<details>
  <summary>Main.java</summary>
  
  ```java
  import zer.exec.EXECTask;
  import zer.exec.EXECResult;
  import zer.exec.EXECResultCode;

  public class Main
  {
    public static void main(String[] args)
    {
      /*  
       * If we don't provide any argument to the "cat"
       * program, it will block the terminal (works
       * like a while true loop), allowing us to see
       * how the timeout works.
       */
       
      EXECResult res = EXECTask.exec("cat", 3000);
      if (res.code() != EXECResultCode.OK)
      {
        System.out.println("[error]: " + res.message());
        return;
      }

      System.out.println(res.message());
    }
  }
  ```
</details>

<details>
  <summary>Result</summary>
  
  ```
  $ javac Main.java
  $ java Main
  [error]: too long.. (more than 3000 ms)
  ```
</details>
