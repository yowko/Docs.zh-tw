---
title: "使用組件設計程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 368021062a3ad49d2c63f92797c59b8c0f1cddfc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="programming-with-assemblies"></a>使用組件設計程式
組件是 .NET Framework 的建置組塊；它們構成部署、版本控制、重複使用、啟用範圍和安全性權限的基礎單位。 組件為通用語言執行平台提供了感知型別實作所需的資訊。 它是建置來共同運作及構成一個功能邏輯單位的類型與資源集合。 對於執行階段而言，型別不會存在於組件的內容以外。  
  
 本節描述如何建立模組、從模組建立組件、建立金鑰組並使用強式名稱來簽署組件，以及將組件安裝到全域組件快取中。 此外，本節還會描述如何使用 [MSIL 反組譯工具 (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢視組件資訊清單資訊。  
  
> [!NOTE]
>  從 .NET Framework 2.0 版開始，執行階段不會載入使用 .NET Framework 版本所編譯的組件，而這個版本的版本號碼高於目前載入的執行階段。 這適用於版本號碼的主要與次要元件組合。  
  
## <a name="in-this-section"></a>本章節內容  
 [建立組件](../../../docs/framework/app-domains/create-assemblies.md)  
 提供單一檔案和多檔案組件的概觀。  
  
 [組件名稱](../../../docs/framework/app-domains/assembly-names.md)  
 提供組件命名概觀。  
  
 [操作說明：決定組件的完整名稱](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 描述如何決定組件的完整名稱。  
  
 [在完全信任環境下執行內部網路應用程式](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 描述如何指定內部網路共用上完全信任組件的舊版安全性原則。  
  
 [組件位置](../../../docs/framework/app-domains/assembly-location.md)  
 提供在何處尋找組件的概觀。  
  
 [操作說明：建置單一檔案組件](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 描述如何建立單一檔案組件。  
  
 [多檔案組件](../../../docs/framework/app-domains/multifile-assemblies.md)  
 描述建立多檔案組件的原因。  
  
 [操作說明：建置多檔案組件](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 描述如何建立多檔案組件。  
  
 [設定組件屬性](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 描述組件屬性和其設定方式。  
  
 [建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 描述如何與為何您使用強式名稱來簽署組件，並包括「如何」主題。  
  
 [延遲簽署組件](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 描述如何延遲簽署組件。  
  
 [使用組件和全域組件快取](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 描述如何與為何您將組件新增至全域組件快取，並包括「如何」主題。  
  
 [操作說明：檢視組件內容](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 描述如何使用 MSIL 反組譯工具 (Ildasm.exe) 來檢視組件內容。  
  
 [Common Language Runtime 中的類型轉送](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 描述如何使用類型轉送將類型移至不同組件，而不會中斷現有應用程式。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Reflection.Assembly>  
 代表組件的 .NET Framework 類別。  
  
## <a name="related-sections"></a>相關章節  
 [操作說明：從組件中取得類型和成員資訊](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 描述如何以程式設計方式從組件中取得類型和其他資訊。  
  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 提供 Common Language Runtime 組件的概念性概觀。  
  
 [組件版本控制](../../../docs/framework/app-domains/assembly-versioning.md)  
 提供組件繫結以及 <xref:System.Reflection.AssemblyVersionAttribute> 和 <xref:System.Reflection.AssemblyInformationalVersionAttribute> 屬性的概觀。  
  
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 描述執行階段如何決定要用哪個組件來實現繫結要求。  
  
 [反映](../../../docs/framework/reflection-and-codedom/reflection.md)  
 描述如何使用「反映」類別，以取得組件的相關資訊。
