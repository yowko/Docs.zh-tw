---
title: "同處理序並存執行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "同處理序並存執行"
  - "並存執行, 同處理序"
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
caps.latest.revision: 25
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 25
---
# 同處理序並存執行
從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]開始，您就可以使用同處理序並存裝載功能，在單一處理序中執行多個 Common Language Runtime \(CLR\) 版本。  根據預設，不論系統針對處理序所載入 .NET Framework 版本為何，Managed COM 元件都會使用建置它們所用的 .NET Framework 版本來執行。  
  
## 背景  
 雖然 .NET Framework 一律會針對 Managed 程式碼應用程式提供並存裝載，但是在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 之前，它並未針對 Managed COM 元件提供該項功能。  在過去，載入處理序中的 Managed COM 元件會使用已經載入的執行階段版本或已安裝的最新 .NET Framework 版本來執行。  如果這個版本與 COM 元件不相容，元件就會失敗。  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 提供了一種達成並存裝載的新方式，可確保下列情況：  
  
-   安裝新的 .NET Framework 版本完全不會影響現有的應用程式。  
  
-   應用程式會針對建置它們所用的 .NET Framework 版本執行。  除非明確指示，否則它們不會使用新的 .NET Framework 版本。  不過，讓應用程式轉換成使用新的 .NET Framework 版本會比較方便。  
  
## 對於使用者和開發人員的影響  
  
-   **使用者和系統管理員**：  這些使用者現在可以更確信，當他們安裝新的執行階段版本時，不論是獨立安裝或與應用程式一起安裝，都完全不會影響他們的電腦。  現有的應用程式將繼續依照先前的方式執行。  
  
-   **應用程式開發人員**：  並存裝載對於應用程式開發人員幾乎沒有任何影響。  根據預設，應用程式一定會針對建置它們所用的 .NET Framework 版本執行。這點不會變更。  不過，開發人員可以覆寫這個行為並且指示應用程式在更新的 .NET Framework 版本底下執行 \(請參閱[案例 2](#scenarios)\)。  
  
-   **程式庫開發人員和消費者**：  並存裝載不會解決程式庫開發人員所面臨的相容性問題。  應用程式直接載入的程式庫 \(透過直接參考或 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 呼叫\) 會繼續使用將它載入其中的 <xref:System.AppDomain> 執行階段。  您應該針對想要支援的所有 .NET Framework 版本測試程式庫。  如果應用程式是使用 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 執行階段所編譯，但是包括使用舊版執行階段所建置的程式庫，該程式庫也會使用 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 執行階段。  不過，如果您擁有使用舊版執行階段所建置的應用程式以及使用 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 所建置的程式庫，就必須強制應用程式使用 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] \(請參閱[案例 3](#scenarios)\)。  
  
-   **Managed COM 元件開發人員**：  在過去，Managed COM 元件會自動使用電腦上已安裝的最新執行階段版本來執行。  不過，您現在可以針對建置 COM 元件所用的執行階段版本執行這些元件。  
  
     如下表所示，雖然使用 .NET Framework 1.1 版所建置的元件可以與 4 版元件並存執行，不過它們無法與 2.0、3.0 或 3.5 版元件一起執行，因為並存裝載不適用於這些版本。  
  
    |.NET Framework 版本|1.1|2.0 \- 3.5|4|  
    |-----------------------|---------|----------------|-------|  
    |1.1|不適用|沒有|有|  
    |2.0 \- 3.5|沒有|不適用|有|  
    |4|有|有|不適用|  
  
> [!NOTE]
>  .NET Framework 3.0 和 3.5 版是根據 2.0 版以累加方式建置的，而且不需要並存執行。  這些原本就是相同的版本。  
  
<a name="scenarios"></a>   
## 常見的並存裝載案例  
  
-   **案例 1**：使用以舊版 .NET Framework 建置之 COM 元件的原生應用程式。  
  
     已安裝的 .NET Framework 版本：[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以及 COM 元件所使用的所有其他 .NET Framework 版本。  
  
     處理方式：在這個案例中，不需要進行任何處理。  COM 元件將使用註冊它們所用的 .NET Framework 版本來執行。  
  
-   **案例 2**：使用 [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] 所建置的 Managed 應用程式，而您想讓此應用程式使用 [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)] 來執行，但是願意讓它在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 上執行 \(如果 2.0 版不存在的話\)。  
  
     已安裝的 .NET Framework 版本：舊版 .NET Framework 和 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]。  
  
     處理方式：在應用程式目錄的[應用程式組態檔](../../../docs/framework/configure-apps/index.md)中，使用 [\<startup\> 項目](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)和 [\<supportedRuntime\> 項目](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)，其設定方式如下：  
  
    ```  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
-   **案例 3**：使用以舊版 .NET Framework 建置之 COM 元件的原生應用程式，而您想要使用 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 來執行此應用程式。  
  
     已安裝的 .NET Framework 版本：[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]。  
  
     處理方式：在應用程式目錄的應用程式組態檔中，使用將 `useLegacyV2RuntimeActivationPolicy` 屬性設定為 `true` 的 `<startup>` 項目和 `<supportedRuntime>` 項目，其設定方式如下：  
  
    ```  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## 範例  
 下列範例將示範一個 Unmanaged COM 主機，它會使用編譯 Managed COM 元件所用的 .NET Framework 版本來執行此元件。  
  
 若要執行下列範例，請編譯和註冊下列使用 [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]的 Managed COM 元件。  若要註冊元件，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]，再按一下 \[**組建**\] 索引標籤，然後選取 \[**註冊 COM Interop**\] 核取方塊。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Runtime.InteropServices;  
  
namespace BasicComObject  
{  
    [ComVisible(true), Guid("9C99C4B5-CA54-4c58-8988-49B6811BA53B")]  
    public class MyObject : SimpleObjectModel.IPrintInfo  
    {  
        public MyObject()  
        {  
        }  
        public void PrintInfo()  
        {  
            Console.WriteLine("MyObject was activated in {0} runtime in:\n\tAppDomain {1}:{2}", System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion(), AppDomain.CurrentDomain.Id, AppDomain.CurrentDomain.FriendlyName);  
        }  
    }  
}  
```  
  
 編譯下列 Unmanaged C\+\+ 應用程式，以便啟動上一個範例所建立的 COM 物件。  
  
```  
#include "stdafx.h"  
#include <string>  
#include <iostream>  
#include <objbase.h>  
#include <string.h>  
#include <process.h>  
  
using namespace std;  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    char input;  
    CoInitialize(NULL) ;  
    CLSID clsid;  
    HRESULT hr;  
    HRESULT clsidhr = CLSIDFromString(L"{9C99C4B5-CA54-4c58-8988-49B6811BA53B}",&clsid);  
    hr = -1;  
    if (FAILED(clsidhr))  
    {  
        printf("Failed to construct CLSID from String\n");  
    }  
    UUID id = __uuidof(IUnknown);  
    IUnknown * pUnk = NULL;  
    hr = ::CoCreateInstance(clsid,NULL,CLSCTX_INPROC_SERVER,id,(void **) &pUnk);  
    if (FAILED(hr))  
    {  
        printf("Failed CoCreateInstance\n");  
    }else  
    {  
        pUnk->AddRef();  
        printf("Succeeded\n");  
    }  
  
    DISPID dispid;  
    IDispatch* pPrintInfo;  
    pUnk->QueryInterface(IID_IDispatch, (void**)&pPrintInfo);  
    OLECHAR FAR* szMethod[1];  
    szMethod[0]=OLESTR("PrintInfo");   
    hr = pPrintInfo->GetIDsOfNames(IID_NULL,szMethod, 1, LOCALE_SYSTEM_DEFAULT, &dispid);  
    DISPPARAMS dispparams;  
    dispparams.cNamedArgs = 0;  
    dispparams.cArgs = 0;  
    VARIANTARG* pvarg = NULL;  
    EXCEPINFO * pexcepinfo = NULL;  
    WORD wFlags = DISPATCH_METHOD ;  
;  
    LPVARIANT pvRet = NULL;  
    UINT * pnArgErr = NULL;  
    hr = pPrintInfo->Invoke(dispid,IID_NULL, LOCALE_USER_DEFAULT, wFlags,  
        &dispparams, pvRet, pexcepinfo, pnArgErr);  
    printf("Press Enter to exit");  
    scanf_s("%c",&input);  
    CoUninitialize();  
    return 0;  
}  
  
```  
  
## 請參閱  
 [\<startup\> 項目](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)   
 [\<supportedRuntime\> 項目](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)