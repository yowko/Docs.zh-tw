---
title: 物件導向程式設計 (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 0dee6edf966e8e2a3e430e60f1c3d51354d08bf3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340589"
---
# <a name="object-oriented-programming-c"></a>物件導向程式設計 (C#)
C# 為包括封裝、繼承和多型在內的物件導向程式設計提供完整支援。  
  
 「封裝」指的是將一組相關的屬性、方法和其他成員，視為單一單位或物件。  
  
 「繼承」則是描述依據現有類別來建立新類別的能力。  
  
 「多型」指的是您可以有多個交替使用的類別，即使每個類別是以不同的方式來實作相同的屬性或方法。  
  
 本節將說明下列概念：  
  
-   [類別與物件](#Classes)  
  
    -   [類別成員](#Members)  
  
         [屬性與欄位](#Properties)  
  
         [方法](#Methods)  
  
         [建構函式](#Constructors)  
  
         [完成項](#Finalizers)  
  
         [事件](#Events)  
  
         [巢狀類別](#NestedClasses)  
  
    -   [存取修飾詞與存取層級](#AccessModifiers)  
  
    -   [具現化類別](#InstantiatingClasses)  
  
    -   [靜態類別與成員](#Static)  
  
    -   [匿名類型](#AnonymousTypes)  
  
-   [繼承](#Inheritance)  
  
    -   [覆寫成員](#Overriding)  
  
-   [介面](#Interfaces)  
  
-   [泛型](#Generics)  
  
-   [委派](#Delegates)  
  
##  <a name="Classes"></a>類別與物件  
 「類別」和「物件」有時會交換使用，但事實上，類別說的是物件的「型別」，而物件則是類別之可使用的「執行個體」。 因此，建立物件的動作稱為「具現化」。 再以藍圖作比喻，若類別是藍圖，物件就是根據藍圖所蓋的建築物。  
  
 若要定義類別：  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 C# 也會提供輕量版的類別，稱為「結構」，當您必須建立龐大物件陣列而不想要使用太多記憶體時，這個結構會很有用。  
  
 若要定義結構：  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 如需詳細資訊，請參閱:  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a> 類別成員  
 每個類別都有不同的「類別成員」，包括描述類別資料的屬性、定義類別行為的方法，以及提供不同類別與物件之間通訊的事件。  
  
####  <a name="Properties"></a> 屬性與欄位  
 欄位和屬性表示物件包含的資訊。 欄位就像是變數，可直接讀取或設定。  
  
 若要定義欄位：  
  
```csharp  
class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 屬性具有取得和設定程序，讓您更容易控制設定與傳回數值的方式。  
  
 C# 允許您建立私用欄位來儲存屬性值，或是使用所謂的自動實作屬性，自動在幕後建立此欄位並提供屬性程序的基本邏輯。  
  
 若要定義自動實作屬性：  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 如果您需要執行某些額外作業來讀取和寫入屬性值，請定義用來儲存屬性值的欄位，並提供儲存和擷取這個欄位的基本邏輯：  
  
```csharp  
class SampleClass  
{  
    private int _sample;  
    public int Sample  
    {  
        // Return the value stored in a field.  
        get { return _sample; }  
        // Store the value in the field.  
        set { _sample = value; }  
    }  
}  
```  
  
 大部分屬性都具有方法或程序，可以設定及取得屬性值。 但是您可以建立唯讀或唯寫屬性來限制不得修改或讀取。 在 C# 中，則可以省略 `get` 或 `set` 屬性方法。 不過，自動實作的屬性不可以是唯讀或唯寫。  
  
 如需詳細資訊，請參閱:  
  
-   [get](../../../csharp/language-reference/keywords/get.md)  
  
-   [set](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a> 方法  
 「方法」是物件可執行的動作。  
  
 若要定義類別的方法：  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 類別可以有同一個方法的多個實作或「多載」，但是這些實作的參數個數和參數類型並不相同。  
  
 若要多載方法：  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 在多數情況下，您是在類別定義中宣告方法。 不過， C# 也支援「擴充方法」，允許您在現有類別的實際定義之外將方法新增至類別。  
  
 如需詳細資訊，請參閱:  
  
-   [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a> 建構函式  
 建構函式是類別方法，會在建立指定類型的物件時自動執行。 建構函式通常用來初始化新物件的資料成員， 而且只能在建立類別時執行一次。 此外，建構函式中的程式碼永遠會在類別中的任何其他程式碼執行之前執行。 不過，就和其他任何方法一樣，您可以建立多個建構函式多載。  
  
 若要定義類別的建構函式：  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 如需詳細資訊，請參閱:  
  
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)。  
  
####  <a name="Finalizers"></a> 完成項  
 完成項是用來解構類別的執行個體。 在 .NET Framework 中，記憶體回收行程會自動管理應用程式中 Managed 物件的記憶體配置及釋放。 不過，您可能仍需要使用完成項來清除應用程式建立的任何 Unmanaged 資源。 一個類別只能有一個完成項。  
  
 如需 .NET Framework 的完成項和記憶體回收的詳細資訊，請參閱[記憶體回收](../../../standard/garbage-collection/index.md)。  
  
####  <a name="Events"></a> 事件  
 事件可讓類別或物件在某些相關的事情發生時，告知其他類別或物件。 傳送 (或引發) 事件的類別稱為「發行者」，而接收 (或處理) 事件的類別則稱為「訂閱者」。 如需事件的詳細資訊以及如何引發和處理事件，請參閱[處理和引發事件](../../../standard/events/index.md)。  
  
-   若要宣告類別中的事件，請使用 [event](../../../csharp/language-reference/keywords/event.md) 關鍵字。  
  
-   要引發事件，請叫用事件委派。  
  
-   若要訂閱事件，請使用 `+=` 運算子；若要取消訂閱事件，則使用 `-=` 運算子。  
  
####  <a name="NestedClasses"></a>巢狀類別  
 在類別中定義的另一個類別即稱為「巢狀」類別。 巢狀類別預設為私用。  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 若要建立巢狀類別的執行個體，請使用容器類別名稱，後面加上點號，再接著巢狀類別名稱，如下所示：  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a> 存取修飾詞與存取層級  
 所有類別及類別成員都可以使用「存取修飾詞」，指定要提供給其他類別的存取層級。  
  
 下列為可用的存取修飾詞：  
  
|C# 修飾詞|定義|  
|------------------|----------------|  
|[public](../../../csharp/language-reference/keywords/public.md)|類型或成員可由相同組件或參考該組件的另一個組件中的任何其他程式碼存取。|  
|[private](../../../csharp/language-reference/keywords/private.md)|類型或成員只能由相同類別中的程式碼存取。|  
|[protected](../../../csharp/language-reference/keywords/protected.md)|類型或成員只能由相同類別中，或是衍生類別中的程式碼存取。|  
|[internal](../../../csharp/language-reference/keywords/internal.md)|類型或成員可由相同組件中的任何程式碼存取，但是不包括其他組件中的程式碼。|  
|[protected internal](../../../csharp/language-reference/keywords/protected-internal.md)|類型或成員可由相同組件中的任何程式碼，或是其他組件中的任何衍生類別存取。|  
|[private protected](../../../csharp/language-reference/keywords/private-protected.md)|只有在基底類別組件中，於相同類別或衍生類別內的程式碼才能存取類型或成員。|  
  
 如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
###  <a name="InstantiatingClasses"></a> 具現化類別  
 若要建立物件，您必須將類別執行個體化，或是建立類別執行個體。  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 將類別執行個體化之後，您就可以將值指派給執行個體的屬性和欄位，並叫用類別方法。  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 若要在類別執行個體化期間將值指派給屬性，請使用物件初始設定式：  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 如需詳細資訊，請參閱:  
  
-   [new 運算子](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a> 靜態類別與成員  
 類別的靜態成員是類別所有執行個體共用的屬性、程序或欄位。  
  
 定義靜態成員：  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 若要存取靜態成員，請使用類別的名稱，但不要建立這個類別的物件：  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 C# 中的靜態類別只有靜態成員，且無法具現化。 靜態成員也無法存取非靜態屬性、欄位或方法  
  
 如需詳細資訊，請參閱[靜態](../../../csharp/language-reference/keywords/static.md)。  
  
###  <a name="AnonymousTypes"></a> 匿名型別  
 使用匿名類型建立物件時，您不需要撰寫資料類型的類別定義， 編譯器 (Compiler) 會自動幫您建立類別 (Class)。 這個類別沒有可使用的名稱，但是包含您在宣告物件時指定的屬性。  
  
 若要建立匿名類型的執行個體：  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 如需詳細資訊，請參閱[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。  
  
##  <a name="Inheritance"></a> 繼承  
 繼承可讓您建立新類別以重複使用、擴充和修改其他類別中定義的行為。 成員被繼承的類別稱為「基底類別」，而繼承這種成員的類別即稱為「衍生類別」。 不過，C# 中的所有類別都隱含繼承 <xref:System.Object> 類別，這個類別會支援 .NET 類別階層架構，並為所有類別提供低階服務。  
  
> [!NOTE]
>  C# 不支援多重繼承。 也就是說，您只能為衍生類別指定一個基底類別。  
  
 若要繼承基底類別：  
  
```csharp  
class DerivedClass:BaseClass{}  
```  
  
 所有類別預設都可以被繼承。 不過，您可以指定類別是否不得當做基底類別，或是建立只能當做基底類別的類別。  
  
 若要指定類別不得當做基底類別使用：  
  
```csharp  
public sealed class A { }  
```  
  
 若要指定類別只能當做基底類別且無法執行個體化：  
  
```csharp  
public abstract class B { }  
```  
  
 如需詳細資訊，請參閱:  
  
-   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a> 覆寫成員  
 衍生類別預設會從其基底類別繼承所有成員。 如果想要變更所繼承成員的行為，您必須覆寫這個成員。 也就是說，您可以定義衍生類別中方法、屬性或事件的新實作。  
  
 下列修飾詞是用來控制如何覆寫屬性及方法：  
  
|C# 修飾詞|定義|  
|------------------|----------------|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|允許在衍生類別中覆寫類別成員。|  
|[override](../../../csharp/language-reference/keywords/override.md)|覆寫在基底類別中定義的虛擬 (可覆寫) 成員。|  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|要求在衍生類別中覆寫類別成員。|  
|[new 修飾詞](../../../csharp/language-reference/keywords/new-modifier.md)|隱藏繼承自基底類別的成員。|  
  
##  <a name="Interfaces"></a> 介面  
 介面就像類別，可定義屬性、方法和事件集。 但與類別不同的是，介面並不提供實作。 介面是由類別實作，並定義為與類別不同的實體。 介面就代表著一種合約，因為實作介面的類別必須完全依介面的定義來實作這個介面的各個方面。  
  
 若要定義介面：  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 若要在類別中實作介面：  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 如需詳細資訊，請參閱:  
  
 [介面](../../../csharp/programming-guide/interfaces/index.md)  
  
 [interface](../../../csharp/language-reference/keywords/interface.md)  
  
##  <a name="Generics"></a> 泛型  
 .NET Framework 中的類別、結構、介面和方法可以包括「型別參數」，這些參數會定義可儲存或使用之物件的類型。 泛型最常見的範例是集合，您可以在其中指定要儲存於集合之物件的類型。  
  
 若要定義泛型類別：  
  
```csharp  
public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 若要建立泛型類別的執行個體：  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 如需詳細資訊，請參閱:  
  
-   [泛型](~/docs/standard/generics/index.md)  
  
-   [泛型](../../../csharp/programming-guide/generics/index.md)  
  
##  <a name="Delegates"></a> 委派  
 「委派」是定義方法簽章的類型，可以提供任何具有相容簽章之方法的參考。 您可以透過委派叫用 (Invoke) 或呼叫方法。 委派可以用來將方法當做引數傳遞給其他方法。  
  
> [!NOTE]
>  事件處理常式就是透過委派叫用的方法。 如需使用委派處理事件的詳細資訊，請參閱[處理和引發事件](../../../standard/events/index.md)。  
  
 若要建立委派：  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 若要建立與委派所指定簽章相符之方法的參考：  
  
```csharp  
class SampleClass  
{  
    // Method that matches the SampleDelegate signature.  
    public static void sampleMethod(string message)  
    {  
        // Add code here.  
    }  
    // Method that instantiates the delegate.  
    void SampleDelegate()  
    {  
        SampleDelegate sd = sampleMethod;  
        sd("Sample string");  
    }  
}  
```  
  
 如需詳細資訊，請參閱:  
  
-   [委派](../../../csharp/programming-guide/delegates/index.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)
