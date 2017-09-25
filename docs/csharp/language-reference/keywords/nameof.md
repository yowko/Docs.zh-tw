---
title: "nameof (C# 參考)"
ms.date: 2017-06-16
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- nameof_CSharpKeyword
- nameof
dev_langs:
- CSharp
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: db79af5f38439b881863cf3e03aa0e684ec5cd39
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="nameof-c-reference"></a>nameof (C# 參考)

用來取得變數、類型或成員的簡單 (不完整) 字串名稱。  

因程式碼發生錯誤、錯誤與模型檢視控制器 (MVC) 連結相互連接，或者錯誤引發了屬性變更事件等狀況而進行回報時，通常還需要擷取方法的字串名稱。  使用 `nameof` 可協助您在重新命名定義時保持程式碼有效。  之前，您必須使用字串常值來參考定義，這在重新命名程式碼項目時很容易損毀，因為工具不知道要檢查這些字串常值。  
  
 `nameof` 運算式的格式如下：  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"  
```  
  
## <a name="key-use-cases"></a>主要使用案例  
 下列範例顯示 `nameof` 的主要使用案例。  
  
 驗證參數：  
 ```csharp  
void f(string s) {  
    if (s == null) throw new ArgumentNullException(nameof(s));  
}  
```  
  
 MVC 動作連結：  
 ```html  
<%= Html.ActionLink("Sign up",  
             @typeof(UserController),  
             @nameof(UserController.SignUp))  
%>  
```  
  
 INotifyPropertyChanged：  
 ```csharp  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
```  
  
 XAML 相依性屬性：  
 ```csharp  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
```  
  
 記錄：  
 ```csharp  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
```  
  
 屬性:   
 ```csharp  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## <a name="examples"></a>範例  
 以下是一些 C# 範例：  
  
```csharp  
using Stuff = Some.Cool.Functionality  
class C {  
    static int Method1 (string x, int y) {}  
    static int Method1 (string x, string y) {}  
    int Method2 (int z) {}  
    string f<T>() => nameof(T);  
}  
  
var c = new C()  
  
nameof(C) -> "C"  
nameof(C.Method1) -> "Method1"   
nameof(C.Method2) -> "Method2"  
nameof(c.Method1) -> "Method1"   
nameof(c.Method2) -> "Method2"  
nameof(z) -> "z" // inside of Method2 ok, inside Method1 is a compiler error  
nameof(Stuff) = "Stuff"  
nameof(T) -> "T" // works inside of method but not in attributes on the method  
nameof(f) -> "f"  
nameof(f<T>) -> syntax error  
nameof(f<>) -> syntax error  
nameof(Method2()) -> error "This expression does not have a name"  
```  
  
## <a name="remarks"></a>備註  
 傳遞給 `nameof` 的引數必須是簡單名稱、限定名稱、成員存取、指定成員的基底存取，或指定成員的這項存取。  引數運算式會識別程式碼定義，但永遠不會加以評估。  
  
 由於引數必須是運算式語法，因此不允許使用許多對清單沒有幫助的項目。  下列項目可能會產生錯誤，值得留意：預先定義的類型 (例如 `int` 或 `void`)、可為 Null 的類型 (`Point?`)、陣列類型 (`Customer[,]`)、指標類型 (`Buffer*`)、限定別名 (`A::B`)、未繫結的泛型類型 (`Dictionary<,>`)、前置處理符號 (`DEBUG`)，以及標籤 (`loop:`)。  
  
 如果您需要取得完整限定名稱，您可以搭配使用 `typeof` 運算式和 `nameof`。  例如: 
```csharp  
class C {
    void f(int i) {  
        Log($"{typeof(C)}.{nameof(f)}", "method entry");  
    }
}
``` 

 可惜，`typeof` 不是 `nameof` 這類常數運算式，因此 `typeof` 不能在 `nameof` 的所有相同位置中搭配使用 `nameof`。  例如，下列情況會導致 CS0182 編譯錯誤：
 ```csharp  
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```    
 報告中有幾個項目能告知我們可能需要處理的問題。  不同於經評估的運算式規定，您不需要具有類型的執行個體。  在某些情況下使用類型名稱會很方便，由於您只參考名稱而不使用執行個體資料，因此不需要設計執行個體變數或運算式。  
  
 您可以在類別的屬性運算式中參考該類別的成員。  
  
 您無法取得簽章資訊，例如 "`Method1 (str, str)`"。  若要執行這項操作，其中一個方法是使用運算式 `Expression e = () => A.B.Method1("s1", "s2")`，然後從產生的運算式樹狀架構中提取 MemberInfo。  
  
## <a name="language-specifications"></a>語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 

