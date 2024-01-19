# Fonksiyonlar

* **Fonksiyonun ismi, yaptığı işi net bir şekilde açıklamalıdır.**


* **Fonksiyonların ilk kuralı; olabildiğince kısa ve odaklı olmalıdır.**

  - Bir fonksiyonun içinde farklı işlemleri yapan kod blokları varsa bunlar parçalanarak
başka fonksiyonlara dağıtılmalıdır. Bu işlem en basitinden okunurluğu kolaylaştıracaktır.


* **Fonksiyonlar bir şey yapmalı ve onu şeyi çok iyi yapmalıdır.**


* **Fonksiyonlada parametre sayısı olabildiğince az tutulmaya çalışılmalı,
    3'ten fazla parametre kullanmamaya özen gösterilmelidir.**

### Fonksiyonlarda Switch Kullanımı

Fonksiyonların içerisinde switch yapılarını kullanarak, direkt nesnenin tipinin konrolünü 
yapmak ve durumlara göre başka fonksiyonları çağırmak kötü bir kullanımdır. Çünkü nesneye her yeni bir tip ya da 
durum eklendiğinde kontrol etmemiz gereken durum sayısı artacaktır. Switch yapısına sürekli ekleme yapılarak uzamasınına neden olacaktır.
Bu şekilde bir kullanım Single Responsibility Principle(Tek Sorumluluk İlkesi) aykırıdır.
Aynı zamanda yapıya her yeni tip eklendiğinde blokta değişiklik yapıldığından dolayı Open Closed Principle uymamaktadır

> [!CAUTION]   
> Aşağıdaki gibi bir kullanımdan kaçınılmalıdır
 >  ```
 >  public Money calculatePay(Employee e)
 >   throws InvalidEmployeeType {
 >      switch (e.type) {
 >          case COMMISSIONED:
 >            return calculateCommissionedPay(e);
 >          case HOURLY:
 >            return calculateHourlyPay(e);
 >          case SALARIED:
 >            return calculateSalariedPay(e);
 >          default:
 >           throw new InvalidEmployeeType(e.type);
 >     }
 >  }
 >  ```

Bunun yerine Abstract Factory Pattern kullanılmalıdır. Bu sayede yeni bir tip oluşturmak gerektiğinde
Employee soyut sınıfından miras alan bir sınıf oluşturulması yeterli olacaktır. Burada switch yapısında
değişiklik yapmaya gerek kalmadan, sistemi genişleteceğiz.

> [!TIP]   
> ABSTRACT FACTORY
>  ```
>     public abstract class Employee {
>      public abstract boolean isPayday();
>       public abstract Money calculatePay();
>       public abstract void deliverPay(Money pay);
>     }
> --------------------
>     public interface EmployeeFactory {
>       public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType;
>     }
> -------------------
>     public class EmployeeFactoryImpl implements EmployeeFactory {
>       public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType {
>           switch (r.type) {
>            case COMMISSIONED:
>              return new CommissionedEmployee(r) ;
>            case HOURLY:
>              return new HourlyEmployee(r);
>            case SALARIED:
>              return new SalariedEmploye(r);
>            default:
>             throw new InvalidEmployeeType(r.type);
>           }
>       }
>     }
>   ```



