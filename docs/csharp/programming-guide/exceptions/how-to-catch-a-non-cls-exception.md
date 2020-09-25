---
title: 如何攔截非 CLS 例外狀況
description: 瞭解如何攔截非 CLS 例外狀況。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: db723cb1e29181e9462c5b423c66cdf8de659259
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178667"
---
# <a name="how-to-catch-a-non-cls-exception"></a>如何攔截非 CLS 例外狀況

包括 C++/CLI 在內的某些 .NET 語言，允許物件擲回非衍生自 <xref:System.Exception> 的例外狀況。 這類例外狀況稱之為「非 CLS 例外狀況」** 或「非例外狀況」**。 在 C# 中無法擲回非 CLS 例外狀況，但有兩種方式可以攔截它們︰  
  
- 在 `catch (RuntimeWrappedException e)` 區塊內。
  
     根據預設，Visual C# 組件會將非 CLS 例外狀況當成包裝例外狀況攔截。 如果您需要存取原始的例外狀況 (它可以透過 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> 屬性存取)，請使用這個方法。 本主題稍後的程序會說明如何以這種方式攔截例外狀況。  
  
- 在一般的 catch 區塊 (不指定例外狀況類型的 catch 區塊) 內，它會放在所有其他 `catch` 區塊的後面。
  
     當您想要執行某些動作 (例如寫入記錄檔) 以回應非 CLS 例外狀況時，請使用這個方法，您不需要存取例外狀況資訊。 Common Language Runtime 預設會包裝所有的例外狀況。 若要停用此行為，請將此組件層級屬性新增至程式碼，通常在 AssemblyInfo.cs 檔案中︰`[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`。  
  
### <a name="to-catch-a-non-cls-exception"></a>攔截非 CLS 例外狀況  
  
在 `catch(RuntimeWrappedException e)` 區塊內，透過 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> 屬性存取原始的例外狀況。  
  
## <a name="example"></a>範例  

 下例示範如何攔截從以 C++/CLI 撰寫的類別庫擲回的非 CLS 例外狀況。 請注意，本例的 C# 用戶端程式碼事先知道被擲回的例外狀況類型是 <xref:System.String?displayProperty=nameWithType>。 您可以將 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> 屬性轉換回原始類型，只要您可從程式碼存取該類型。  
  
```csharp
// Class library written in C++/CLI.
var myClass = new ThrowNonCLS.Class1();

try
{
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();
}
catch (RuntimeWrappedException e)
{
    String s = e.WrappedException as String;
    if (s != null)
    {
        Console.WriteLine(s);
    }
}
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [例外狀況和例外狀況處理](./index.md)
