---
title: 使用組件和全域組件快取
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 363410baea1706211acaa639f1704e91230723a8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592726"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a>使用組件和全域組件快取
如果您想要在數個應用程式之間共用組件，可以將它安裝到全域組件快取。 每部安裝 Common Language Runtime 的電腦都有這個全機器程式碼快取。 全域組件快取會儲存特別指定為由電腦上數個應用程式共用的組件。 組件必須有強式名稱，才能安裝在全域組件快取中。  
  
> [!NOTE]
>  放在全域組件快取中的組件必須具有相同的組件名稱和檔案名稱 (不包括副檔名)。 例如，組件名稱為 myAssembly 之組件的檔案名稱必須有 myAssembly.exe 或 myAssembly.dll。  
  
 您應該只有在必要時才將組件安裝到全域組件快取，來共用組件。 一般來說，除非明確需要共用組件，否則會將組件相依性保留為私用，並且在應用程式目錄中尋找組件。 此外，您不需要將組件安裝到全域組件快取，它們即可供 COM Interop 或 Unmanaged 程式碼使用。  
  
 您有數個原因想要將組件安裝到全域組件快取中：  
  
- 共用位置。  
  
     應用程式應該使用的組件可以放在全域組件快取中。 例如，如果所有應用程式都應該使用位於全域組件快取中的組件，則可以將版本原則陳述式新增至 Machine.config 檔案，以將參考重新導向至組件。  
  
- 檔案安全性。  
  
     系統管理員通常會使用存取控制清單 (ACL) 來控制寫入和執行存取權，以便保護 systemroot 目錄。 因為全域組件快取安裝在 systemroot 目錄中，所以它會繼承該目錄的 ACL。 建議只有具備系統管理員權限的使用者能從全域組件快取刪除檔案。  
  
- 並存版本。  
  
     具有相同名稱但不同版本資訊之組件的多個複本，可以在全域組件快取中進行維護。  
  
- 其他搜尋位置。  
  
     在探查或使用組態檔中的程式碼基底資訊之前，Common Language Runtime 會檢查全域組件快取中是否有符合組件要求的組件。  
  
 請注意，有些情況下您明確不想要將組件安裝到全域組件快取中。 如果您將構成應用程式的其中一個組件放入全域組件快取中，則可以使用 XCOPY 複製應用程式目錄，以不再複寫或安裝應用程式。 在此情況下，您也必須將組件移至全域組件快取。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：在全域組件快取中安裝單一組件](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 描述將組件安裝到全域組件快取中的方式。  
  
 [如何：檢視全域組件快取的內容](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 說明如何使用 [Gacutil.exe (全域組件快取工具)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 來檢視全域組件快取的內容。  
  
 [如何：從全域組件快取移除組件](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 說明如何使用 [Gacutil.exe (全域組件快取工具)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 來移除全域組件快取中的組件。  
  
 [使用 Serviced 元件和全域組件快取](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 說明 Serviced 元件 (Managed COM+ 元件) 為何應該放在全域組件快取中。  
  
## <a name="related-sections"></a>相關章節  
 [建立組件](../../../docs/framework/app-domains/create-assemblies.md)  
 提供建立組件的概觀。  
  
 [全域組件快取](../../../docs/framework/app-domains/gac.md)  
 描述全域組件快取。  
  
 [如何：檢視組件內容](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 說明如何使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢視組件中的 Microsoft 中繼語言 (MSIL) 資訊。  
  
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 描述 Common Language Runtime 如何找出和載入構成應用程式的組件。  
  
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 描述組件，即 Managed 應用程式的建置組塊。
