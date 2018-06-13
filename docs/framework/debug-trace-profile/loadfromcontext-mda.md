---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e1ba65194c49f76bb5c29ed28b1b038c02cf1a59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393077"
---
# <a name="loadfromcontext-mda"></a>loadFromContext MDA
如果組件載入到 `LoadFrom` 內容中，就會啟動 `loadFromContext` Managed 偵錯助理 (MDA)。 這種情況可能是因為呼叫 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 或其他類似方法而發生。  
  
## <a name="symptoms"></a>徵兆   
 使用某些載入器方法可能會將組件載入到 `LoadFrom` 內容中。 使用這個內容可能會導致序列化、轉型和相依性解析的未預期行為。 一般情況下，建議將組件載入至 `Load` 內容，以避免這些問題發生。 無此 MDA，難以判斷哪些內容已載入組件。  
  
## <a name="cause"></a>原因  
 一般而言，如果組件是從 `Load` 內容的外部路徑載入，例如全域組件快取或 <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> 屬性，就會載入至 `LoadFrom` 內容。  
  
## <a name="resolution"></a>解決方式  
 設定應用程式，因此不再需要 <xref:System.Reflection.Assembly.LoadFrom%2A> 呼叫。 您可以使用下列技巧執行該作業：  
  
-   在全域組件快取中安裝組件。  
  
-   將組件放置在 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A>目錄中。 如果是預設網域，<xref:System.AppDomainSetup.ApplicationBase%2A> 目錄會包含啟動處理序的可執行檔。 如果移動組件不方便，可能也需要建立新的 <xref:System.AppDomain>。  
  
-   如果相依組件位在可執行檔的相對子目錄中，請將探查路徑新增至應用程式組態檔 (.config) 或次要應用程式網域。  
  
 每個案例都可以變更程式碼，以使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 MDA 對 CLR 不會產生任何影響。 它報告的內容，過去用為載入要求的結果。  
  
## <a name="output"></a>輸出  
 MDA 會報告組件已載入至 `LoadFrom` 內容。 它會指定組件和路徑的簡單名稱。 也會建議降低風險，避免使用 `LoadFrom` 內容。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例示範可啟用此 MDA 的情況：  
  
```  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is   
            // located outside of the Load context probing path.   
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
