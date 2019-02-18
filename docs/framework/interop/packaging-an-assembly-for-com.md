---
title: 封裝 COM 的組件
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d51fcbdeeaa1fe30bbdeff5eb85a1c15fa9b4847
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221078"
---
# <a name="packaging-an-assembly-for-com"></a>封裝 COM 的組件
COM 開發人員可以獲益於他們要併入其應用程式之 Managed 類型的下列資訊：  
  
-   COM 應用程式可使用的類型清單  
  
     COM 看不到一些 Managed 類型、有些看得到但無法建立，但有些是可見並可建立。 組件可以包含任意的不可見、可見、不可建立和可建立類型組合。 為求完整性，識別組件中想要公開至 COM 的類型，特別是這些類型是公開至 .NET Framework 之類型的子集。  
  
     如需詳細資訊，請參閱[限定交互操作的 .NET 類型](qualifying-net-types-for-interoperation.md)。  
  
-   版本設定指示  
  
     可實作類別介面 (COM Interop 產生的介面) 的 Managed 類別受到版本設定限制。  
  
     如需使用類別介面的方針，請參閱[類別介面簡介](com-callable-wrapper.md#introducing-the-class-interface)。  
  
-   部署指示  
  
     發行者所簽署的強式名稱組件可以安裝到全域組件快取。 未簽署的組件必須安裝在使用者電腦上，當成私用組件。  
  
     如需詳細資訊，請參閱[組件安全性考量](../app-domains/assembly-security-considerations.md)。  
  
-   型別程式庫包含  
  
     COM 應用程式使用時，大部分類型都需要型別程式庫。 您可以產生型別程式庫，或讓 COM 開發人員執行這項工作。 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 提供下列選項來產生型別程式庫：  
  
    -   [型別程式庫匯出工具](#cpconpackagingassemblyforcomanchor1)  
  
    -   [TypeLibConverter 類別](#cpconpackagingassemblyforcomanchor2)  
  
    -   [組件註冊工具](#cpconpackagingassemblyforcomanchor3)  
  
    -   [.NET 服務安裝工具](#cpconpackagingassemblyforcomanchor4)  
  
     不論您選擇的機制為何，只有所提供組件中定義的公用類型才會包含在所產生的型別程式庫中。  
  
     您可以將型別程式庫包裝為個別檔案，或將它當成 Win32 資源檔內嵌在 .NET 架構應用程式內。 Microsoft Visual Basic 6.0 已自動為您執行這項工作；不過，使用 [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] 時，您必須手動內嵌型別程式庫。 如需相關指示，請參閱[如何：將型別程式庫當作 Win32 資源內嵌在 .NET 架構應用程式中](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))。  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a>類型程式庫匯出工具  
 [型別程式庫匯出工具 (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) 是一種命令列工具，可將組件中所含的類別和介面轉換成 COM 型別程式庫。 有類別的類型資訊可用之後，COM 用戶端就可以建立 .NET 類別執行個體，並呼叫執行個體的方法，就像它是 COM 物件一樣。 Tlbexp.exe 一次會轉換整個組件。 您無法使用 Tlbexp.exe 來為組件中所定義的類型子集產生類型資訊。  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a>TypeLibConverter 類別  
 位於 **System.Runtime.Interop** 命名空間中的 <xref:System.Runtime.InteropServices.TypeLibConverter> 類別會將組件中所含的類別和介面轉換成 COM 型別程式庫。 此 API 會產生與型別程式庫匯出工具相同的類型資訊 (如上節所述)。  
  
 **TypeLibConverter class** 實作 <xref:System.Runtime.InteropServices.ITypeLibConverter>。  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a>組件註冊工具  
 當您套用 **/tlb:** 選項時，[組件註冊工具 (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) 可以產生和註冊型別程式庫。 COM 用戶端需要在 Windows 登錄中安裝型別程式庫。 沒有這個選項時，Regasm.exe 只會在組件中註冊類型，而不是型別程式庫。 在組件中註冊類型以及在型別程式庫中註冊類型是不同的活動。  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a>.NET 服務安裝工具  
 [.NET 服務安裝工具 (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) 會將 Managed 類別新增至 Windows 2000 元件服務，並將數項工作合併到單一工具。 除了載入和註冊組件之外，Regsvcs.exe 還可以在現有 COM+ 1.0 應用程式中產生、註冊和安裝型別程式庫。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [將 .NET Framework 元件公開給 COM](exposing-dotnet-components-to-com.md)
- [限定互通的 .NET 類型](qualifying-net-types-for-interoperation.md)
- [類別介面簡介](com-callable-wrapper.md#introducing-the-class-interface)
- [組件安全性考量](../app-domains/assembly-security-considerations.md)
- [Tlbexp.exe (類型程式庫匯出工具)](../tools/tlbexp-exe-type-library-exporter.md)
- [向 COM 註冊組件](registering-assemblies-with-com.md)
- [如何：將型別程式庫當作 Win32 資源內嵌在應用程式中](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))
