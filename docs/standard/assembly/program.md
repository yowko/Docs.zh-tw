---
title: 具有元件的程式
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03babe701b46eab54a76094c4728af80e6d9911e
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973135"
---
# <a name="program-with-assemblies"></a>具有元件的程式
組件是 .NET Framework 的建置組塊；它們構成部署、版本控制、重複使用、啟用範圍和安全性權限的基礎單位。 組件為通用語言執行平台提供了感知型別實作所需的資訊。 它是建置來共同運作及構成一個功能邏輯單位的類型與資源集合。 對於執行階段而言，型別不會存在於組件的內容以外。  
  
 本節描述如何建立模組、從模組建立組件、建立金鑰組並使用強式名稱來簽署組件，以及將組件安裝到全域組件快取中。 此外，本節還會描述如何使用 [MSIL 反組譯工具 (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) 來檢視組件資訊清單資訊。  
  
> [!NOTE]
> 從 .NET Framework 2.0 版開始，執行階段不會載入使用 .NET Framework 版本所編譯的組件，而這個版本的版本號碼高於目前載入的執行階段。 這適用於版本號碼的主要與次要元件組合。  
  
## <a name="in-this-section"></a>本節內容  
 [建立元件](create.md)  
 提供單一檔案和多檔案組件的概觀。  
  
 [元件名稱](names.md)  
 提供組件命名概觀。  
  
 [如何：決定元件的完整名稱](find-fully-qualified-name.md)  
 描述如何決定組件的完整名稱。  
  
 [以完全信任的方式執行內部網路應用程式](../../framework/app-domains/running-intranet-applications-in-full-trust.md)  
 描述如何指定內部網路共用上完全信任組件的舊版安全性原則。  
  
 [元件位置](location.md)  
 提供在何處尋找組件的概觀。  
  
 [如何：建立單一檔案元件](../../framework/app-domains/build-single-file-assembly.md)  
 描述如何建立單一檔案組件。  
  
 [多檔案元件](../../framework/app-domains/multifile-assemblies.md)  
 描述建立多檔案組件的原因。  
  
 [如何：建立多檔案元件](../../framework/app-domains/build-multifile-assembly.md)  
 描述如何建立多檔案組件。  
  
 [設定組件屬性](set-attributes.md)  
 描述組件屬性和其設定方式。  
  
 [建立和使用強式名稱的元件](create-use-strong-named.md)  
 描述如何與為何您使用強式名稱來簽署組件，並包括「如何」主題。  
  
 [延遲簽署元件](delay-sign.md)  
 描述如何延遲簽署組件。  
  
 [使用元件和全域組件快取](../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 描述如何與為何您將組件新增至全域組件快取，並包括「如何」主題。  
  
 [如何：視圖元件內容](view-contents.md)  
 描述如何使用 MSIL 反組譯工具 (Ildasm.exe) 來檢視組件內容。  
  
 [Common language runtime 中的類型轉送](type-forwarding.md)  
 描述如何使用類型轉送將類型移至不同組件，而不會中斷現有應用程式。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Reflection.Assembly>  
 代表組件的 .NET Framework 類別。  
  
## <a name="related-sections"></a>相關章節  
 [如何：從元件中取得類型和成員資訊](../../framework/reflection-and-codedom/get-type-member-information.md)  
 描述如何以程式設計方式從組件中取得類型和其他資訊。  
  
 [.NET 中的組件](index.md)  
 提供 Common Language Runtime 組件的概念性概觀。  
  
 [元件版本控制](versioning.md)  
 提供組件繫結以及 <xref:System.Reflection.AssemblyVersionAttribute> 和 <xref:System.Reflection.AssemblyInformationalVersionAttribute> 屬性的概觀。  
  
 [執行階段如何找出組件](../../framework/deployment/how-the-runtime-locates-assemblies.md)  
 描述執行階段如何決定要用哪個組件來實現繫結要求。  
  
 [反映](../../framework/reflection-and-codedom/reflection.md)   
 描述如何使用「反映」類別，以取得組件的相關資訊。
