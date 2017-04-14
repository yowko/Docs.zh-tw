---
title: "封裝 COM 的組件 | Microsoft Docs"
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
  - ".NET 服務安裝工具"
  - "組件註冊工具"
  - "COM Interop, 公開 COM 元件"
  - "COM Interop, 封裝組件"
  - "將 .NET Framework 元件公開給 COM"
  - "與 Unmanaged 程式碼的互通, 公開 .NET Framework 元件"
  - "與 Unmanaged 程式碼的互通, 封裝組件"
  - "為 COM 封裝組件"
  - "Reqasm.exe"
  - "Reqsvcs.exe"
  - "Tlbexp.exe"
  - "類型程式庫匯出工具"
  - "TypeLibConverter 類別"
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 封裝 COM 的組件
對於打算將 Managed 型別加入到應用程式的 COM 開發者，下列相關可能會有所幫助：  
  
-   COM 應用程式可使用之型別的清單  
  
     有些 Managed 型別是 COM 看不見的；有些是看得見卻不能建立；而另一些則是看得見而且也可以建立。  組件可以由可顯示、不可顯示、可建立或不可建立等型別的各種組合方式所組成。  為了完整起見，請識別組件中您想要公開給 COM 的型別，尤其是當這些型別是公開給 .NET Framework 之型別的子集時。  
  
     如需詳細資訊，請參閱[限定互通的 .NET 型別](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)。  
  
-   版本指示  
  
     實作類別介面 \(由 COM Interop 產生的介面\) 的 Managed 類別須受版本的限制。  
  
     如需使用類別介面的方針，請參閱[類別介面簡介](http://msdn.microsoft.com/zh-tw/733c0dd2-12e5-46e6-8de1-39d5b25df024)。  
  
-   部署指示  
  
     由發行者簽名，強式名稱的組件可以安裝到全域組件快取中。  未簽名的組件必須安裝到使用者的電腦上做為私用組件。  
  
     如需詳細資訊，請參閱[組件安全性考量](../../../docs/framework/app-domains/assembly-security-considerations.md)。  
  
-   型別程式庫含入  
  
     COM 應用程式在使用大部分型別時都需要型別程式庫。  您可以產生一個型別程式庫，或是讓 COM 開發者執行這項工作。  [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 提供下列產生型別程式庫的選項：  
  
    -   [型別程式庫匯出工具](#cpconpackagingassemblyforcomanchor1)  
  
    -   [TypeLibConverter 類別](#cpconpackagingassemblyforcomanchor2)  
  
    -   [組件註冊工具](#cpconpackagingassemblyforcomanchor3)  
  
    -   [.NET 服務安裝工具](#cpconpackagingassemblyforcomanchor4)  
  
     不論您選擇哪種機制，只有您所提供組件中定義的公用型別會包括在產生的型別程式庫中。  
  
     您可以將型別程式庫封裝為不同的檔案，或將其嵌入為 .NET 架構應用程式中的 Win32 資源檔。  Microsoft Visual Basic 6.0 會自動執行此項工作；但是，當使用 [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] 時，則必須以手動方式嵌入型別程式庫。  如需相關說明，請參閱 [HOW TO：將型別程式庫當做 Win32 資源內嵌在 .NET 架構應用程式中](http://msdn.microsoft.com/zh-tw/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44)。  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## 型別程式庫匯出工具  
 [型別程式庫匯出工具 \(Tlbexp.exe\)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) 是一種命令列工具，可以將組件中包含的類別和介面轉換為 COM 型別程式庫。  一旦有了類別的型別資訊，COM 用戶端就可以建立 .NET 類別的執行個體，並且呼叫這個執行個體上的方法，就如同它是 COM 物件一樣。  Tlbexp.exe 會一次轉換整個組件。  您無法使用 Tlbexp.exe 來為組件中所定義的型別子集產生型別資訊。  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## TypeLibConverter 類別  
 **System.Runtime.Interop** 命名空間中的 <xref:System.Runtime.InteropServices.TypeLibConverter> 類別會將組件中所含的類別和介面轉換為 COM 型別程式庫。  這個 API 會產生與型別程式庫匯出工具同樣的型別資訊，如前一節中所描述。  
  
 **TypeLibConverter** 類別會實作 [ITypeLibConverter 介面](frlrfSystemRuntimeInteropServicesITypeLibConverterClassTopic)。  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## 組件註冊工具  
 在套用 **\/tlb:** 選項時，[組件註冊工具 \(Regasm.exe\)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) 會產生和註冊型別程式庫。  COM 用戶端要求型別程式庫必須安裝在 Windows 登錄中。  不用這個選項的話，Regasm.exe 只會註冊組件中的型別，不會註冊型別程式庫。  註冊組件的型別和註冊型別程式庫是明顯不同的活動。  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## .NET 服務安裝工具  
 [.NET 服務安裝工具 \(Regsvcs.exe\)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md) 會將 Managed 類別加入到 Windows 2000 元件服務，並且在單一工具中結合了好幾項工作。  除了載入和註冊組件之外，Regsvcs.exe 還可以產生、註冊和安裝型別程式庫到現有的 COM\+ 1.0 應用程式。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.TypeLibConverter>   
 <xref:System.Runtime.InteropServices.ITypeLibConverter>   
 [將 .NET Framework 元件公開給 COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [限定互通的 .NET 類型](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)   
 [Introducing the Class Interface](http://msdn.microsoft.com/zh-tw/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [組件安全性考量](../../../docs/framework/app-domains/assembly-security-considerations.md)   
 [Tlbexp.exe \(Type Library Exporter\)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)   
 [向 COM 註冊組件](../../../docs/framework/interop/registering-assemblies-with-com.md)   
 [How to: Embed Type Libraries as Win32 Resources in Applications](http://msdn.microsoft.com/zh-tw/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44)