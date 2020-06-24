# III-hafta-odevi


1.Task vs process- task vs Thread vs .. ve c# task vs thread vs .. kıyaslamalarını ve task haricinde diğer yöntemler nelerdir araştırınız.
2.Extension Nedir? --> Extra paket ekleme. <br/>
3.SQLite, bunu doğru şekilde (en güncel yol ile) nasıl kullanmalıyız? (Aktif halde kullanıp uygulama)


## Lastpast/Serverless

- [https://github.com/GeekG1rl/slack-lastpass/blob/master/serverless.yml]: 

  ## Azure Logic Apps

  - Bir bulut hizmetidir.Bir dizi API'yi tüketme kolaylığı olarak tanımlar.

  - Logic Apps, bulutta, şirket içinde veya her ikisinde de olmak üzere uygulama [tümleştirme](https://azure.microsoft.com/product-categories/integration/), veri tümleştirmesi, sistem tümleştirmesi, kurumsal uygulama TÜMLEŞTIRME (EAI) ve şletmeler arası (B2B) iletişim için ölçeklenebilir çözümler tasarlama ve oluşturma işlemlerini basitleştirir.

    ## Azure Funtions

  - Kullanıcının altyapı sağlamak veya yönetmek zorunda kalmadan olayla tetiklenen kodu çalıştırmasını sağlayan sunucusuz bir bilgi işlem hizmetidir.

  - Çeşitli olaylara yanıt olarak bir komut dosyası veya kod parçası çalıştırır.



## .gitignore Nedir?

-  Git'e hangi dosyaları(veya desenleri) yok sayması gerektiğini söyler. Yararlı olmayan geçici dosyaları çalışma dizininizden almaktan kaçınmak için kullanılır.

## Stashes Nedir?

- **git stash** ile üzerinde çalıştığınız ancak henüz commit etmediğiniz değişikliklerin geçici olarak Git tarafından kayıt altına alınmasını ve aktif branch'inizin herhangi bir değişikliğin olmadığı temiz bir duruma getirilmesini sağlar.



## Nullable Tipler Nedir?

- İlgili tip'in değer aralığına ve karakteristliğine sahip olmakla birlikte ek olarak **null** değer de içerebilen yapılardır. Basit olarak, değişkenin değer içerip içermediği bilgisini saklar.

[https://docs.microsoft.com/tr-tr/dotnet/csharp/language-reference/builtin-types/nullable-value-types]: 



## Task Haricindeki Diğer Yöntemler



#### TASK vs Process

[https://tallyfy.com/task-vs-project-vs-process-management/]: 



#### TASK vs ValueTask

[https://docs.microsoft.com/tr-tr/dotnet/api/system.threading.tasks.valuetask-1?view=netcore-3.1]: 

#### TASK vs Thread

Task yapısı thread yapısından üst seviyededir.Task yapısı daha gelişmiştir.

[https://docs.microsoft.com/tr-tr/dotnet/api/system.threading.tasks?view=netcore-3.1]: 

#### TASK vs Parallel

[https://docs.microsoft.com/tr-tr/dotnet/api/system.threading.tasks.parallel?view=netcore-3.1]: 

## Extension Metod Nedir? Nasıl Yazılır ?

- Extension metodlar herhangi bir yeni nesne oluşturmadan, üzerinde işlem yaptığımız nesne üzerinde çağrılabilen "genişletilmiş" manasına gelen pratik metodlardır.

- Bizi sürekli aynı kodları yazmaktan kurtarır.

- Statik metodlar ve statik classlardan oluşur.Referans olarak oluşturduğumuz obje üzerinden çağrılır.

  xtension metodların aldığı ilk parametre, bu metodun hangi nesne üzerinde çalışacağını belirtir. Ve alacağı ilk parametrenin önüne "this" anahtar kelimesi getirilir. Böylece metodun bu nesne üzerinde işlem yapacağı belirtilmiş olur.

  Extension metodların kullanımı da çok kolaydır. Extension metodları kullanacağınız kaynak koda, using anahtar kelimesini kullanarak eklediğinizde bu metodlarınızı kullanabilirsiniz. Bu kadar açıklamadan sonra artık uygulamaya geçebiliriz.

  Extension metod eklemenin ilk adımı normal bir class ekler gibi projemize class ekliyoruz. Ben extension metodlarımı saklamak için kullanacağım classa HelpExtensions adını vereceğim. Eklediğimiz bu class statik olmak zorunda. Ve daha sonra yukarıdaki yönergelere uygun şekilde metodlarımızı yazabiliriz. 

  ```cs
  using System;
  using System.Collections.Generic;
  using System.Linq;
  using System.Text;
  using System.Threading.Tasks;
  
  namespace FvrNews.Library.CustomModels.Extensions {
      public static class HelpExtensions {
  
          public static int ToInt32(this string s) {
              return Convert.ToInt32(s);
          }
      }
  }
  ```

  Yukarıdaki kodu inceleyecek olursak, bahsettiğim gibi HelpExtensions adında bir class oluşturdum. Dikkat ederseniz classım statik. Daha sonra bu metodun string tipindeki değerler üzerinde kullanılacağını belirttim, metoda verdiğim parametrenin önüne this anahtar kelimesini getirerek(this string s). Geri dönüş tipi olarak ta int olduğunu belirttim.

  Bu metodu yazarak her defasında string bir değeri int değere çevirmek için kod yazmakla uğraşmayacağım. String nesne üzerinden ToInt32 metodunu kullanarak direkt geri dönen değeri alabileceğim. Aşağıda da metodun kullanım biçimini görebilirsiniz.

  ```cs
  using System.Linq;
  using System.Web.Mvc;
  using FvrNews.Library.CustomModels.Extensions; //Extension metodumun bulunduğu namespace
  using FvrNews.Library.Services;
  
  namespace TheLira.Controllers {
      public class PageController : Controller {
          public ActionResult GetPage(string pageSefLink,string[] idArray) {
  
              //String nesne üzerinden çağırdığım ToInt32 metodu
              int firstId = idArray.First().ToInt32();
              
              return View(new PageService().GetPageByID(firstId));
          }
      }
  }
  ```





[http://www.yavuzaydogan.com/c-sharp/extension-metod-nedir-nasil-yazilir-nasil-kullanilir-147]: 

