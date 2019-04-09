---
title: bindingFailure MDA
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 88f23c2e03966bffccc9153e18e1b54e6847987d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127604"
---
# <a name="bindingfailure-mda"></a>bindingFailure MDA
無法載入組件時，會啟用 `bindingFailure` Managed 偵錯助理 (MDA)。  
  
## <a name="symptoms"></a>徵兆  
 程式碼已嘗試使用靜態參考或其中一個載入器方法 (例如 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 或 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>) 載入組件。 未載入組件，並擲回 <xref:System.IO.FileNotFoundException> 或 <xref:System.IO.FileLoadException> 例外狀況。  
  
## <a name="cause"></a>原因  
 執行階段無法載入組件時，發生繫結失敗。 繫結失敗可能是下列其中一個情況所造成：  
  
-   Common Language Runtime (CLR) 找不到要求的組件。 有許多原因可能會發生這種情況，例如未安裝組件，或應用程式未正確地設定成尋找組件。  
  
-   常見問題案例是將類型傳遞給另一個應用程式定義域，而這需要 CLR 在另一個應用程式定義域中載入包含該類型的組件。 如果另一個應用程式定義域與原始應用程式定義域的設定方式不同，則執行階段可能無法載入組件。 例如，兩個應用程式定義域可能會有不同的 <xref:System.AppDomain.BaseDirectory%2A> 屬性值。  
  
-   所要求的組件損毀或不是組件。  
  
-   嘗試載入組件的程式碼沒有載入組件的正確程式碼存取安全性權限。  
  
-   使用者認證未提供讀取檔案的必要權限。  
  
## <a name="resolution"></a>解決方式  
 第一個步驟是判斷 CLR 為什麼無法繫結至所要求的組件。 有許多原因會找不到執行階段或無法載入所要求的組件，例如 [原因] 區段中列出的案例。 若要消除繫結失敗的原因，建議使用下列動作：  
  
-   使用 `bindingFailure` MDA 所提供的資料，來判斷原因：  
  
    -   執行 [Fuslogvw.exe (組件繫結記錄檔檢視器)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)，以讀取組件繫結器所產生的錯誤記錄檔。  
  
    -   判斷組件是否位於要求的位置。 如果是 <xref:System.Reflection.Assembly.LoadFrom%2A> 和 <xref:System.Reflection.Assembly.LoadFile%2A> 方法，則可以輕鬆地判斷所要求的位置。 如果是使用組件身分識別繫結的 <xref:System.Reflection.Assembly.Load%2A> 方法，則您必須尋找符合應用程式定義域之 <xref:System.AppDomain.BaseDirectory%2A> 屬性探查路徑和全域組件快取中該身分識別的組件。  
  
-   根據先前的判斷來解決原因。 可能的解決方式選項如下：  
  
    -   在全域組件快取中安裝所要求的組件，並呼叫 <xref:System.Reflection.Assembly.Load%2A> 若要依身分識別載入組件的方法。  
  
    -   將所要求的組件複製至應用程式目錄，並呼叫 <xref:System.Reflection.Assembly.Load%2A> 方法，依身分識別載入組件。  
  
    -   變更 <xref:System.AppDomain.BaseDirectory%2A> 屬性，或新增私用探查路徑，以重新設定發生繫結失敗的應用程式定義域，來包含組件路徑。  
  
    -   變更檔案的存取控制清單，讓已登入的使用者讀取檔案。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。 它只會回報繫結失敗的資料。  
  
## <a name="output"></a>Output  
 MDA 回報無法載入的組件，包含要求的路徑和 (或) 顯示名稱、繫結內容、在其中要求載入的應用程式定義域，以及失敗原因。  
  
 如果該資料無法用於 CLR，則顯示名稱或所要求的路徑可能空白。 如果失敗的呼叫是 <xref:System.Reflection.Assembly.Load%2A> 方法，則執行階段可能無法判斷組件的顯示名稱。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例示範可啟用此 MDA 的情況：  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // This call attempts to load a nonexistent assembly.  
            // The call will throw a System.IO.FileNotFound exception  
            // and cause the activation of the bindingFailure MDA   
            // if it is registered.  
            Assembly.Load("NonExistentAssembly");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
