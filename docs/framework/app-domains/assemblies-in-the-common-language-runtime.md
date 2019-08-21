---
title: Common Language Runtime 中的組件
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.assetid: 2cfebe19-7436-49f1-bd99-3c4019f0b676
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b27a8d89b0345082b8cf06c3eb141e73e2bf0faf
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567357"
---
# <a name="assemblies-in-the-common-language-runtime"></a>Common Language Runtime 中的組件
組件是 .NET Framework 應用程式的建置組塊；它們構成部署、版本控制、重複使用、啟用範圍和安全性權限的基礎單位。 組件是建置來共同運作及構成一個功能邏輯單位的型別與資源集合。 組件為通用語言執行平台提供了感知型別實作所需的資訊。 對於執行階段而言，型別不會存在於組件的內容以外。  
  
 組件可以執行以下功能：  
  
- 組件包含通用語言執行平台執行的程式碼。 如果組件沒有相關聯的組件資訊清單，則不會執行可攜式執行檔 (PE) 中的 Microsoft 中繼語言 (MSIL) 程式碼。 請注意，每個組件只能有一個進入點 (`DllMain`、`WinMain` 或 `Main`)。  
  
- 組件可構成安全性界限。 組件是要求和授與權限的單位。 如需套用至組件之安全性界限的詳細資訊，請參閱[組件安全性考量](../../../docs/framework/app-domains/assembly-security-considerations.md)。  
  
- 組件可構成型別界限。 每種型別的識別都包含該型別所在之組件的名稱。 在某個組件範圍中載入的型別 `MyType` 與在另一個組件範圍中載入的型別 `MyType` 不同。  
  
- 組件可構成參考範圍界限。 組件的資訊清單含有用來解析型別和滿足資源要求的組件中繼資料。 它會指定公開於組件之外的型別和資源。 資訊清單也會列舉組件相依的其他組件。  
  
- 組件可構成版本界限。 組件是通用語言執行平台中可控制版本的最小單位；在同一組件中的所有型別和資源會當做一個單位來控制版本。 組件的資訊清單描述您對任何相依組件所指定的版本相依性。 如需版本控制的詳細資訊，請參閱[組件版本控制](../../../docs/framework/app-domains/assembly-versioning.md)。  
  
- 組件可構成部署單位。 當應用程式啟動時，一定要有應用程式一開始所呼叫的組件。 至於其他組件 (例如當地語系化資源或含有公用程式類別的組件)，則可視需要擷取。 如此可讓應用程式在第一次下載時保持最簡狀態。 如需部署組件的詳細資訊，請參閱[部署應用程式](../../../docs/framework/deployment/index.md)。  
  
- 組件是支援並存執行的單位。 如需執行多個組件版本的詳細資訊，請參閱[組件和並存執行](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)。  
  
 組件可以是靜態，也可以是動態。 靜態組件可以包含 .NET Framework 型別 (介面和類別)，以及組件的資源 (點陣圖、JPEG 檔案、資源檔案等)。 靜態組件儲存在磁碟上的可攜式執行檔 (PE) 中。 您也可以使用 .NET Framework 建立動態組件，直接從記憶體執行，並且執行前不會儲存至磁碟。 您可以在執行動態組件之後，再將其儲存至磁碟。  
  
 您可以使用幾種方式建立組件。 您可以使用過去用來建立 .dll 或 .exe 檔案的開發工具，例如 Visual Studio。 您可以使用 Windows SDK 中提供的工具，搭配其他開發環境中建立的模組來建立組件。 您也可以使用 Common Language Runtime API (例如 <xref:System.Reflection.Emit?displayProperty=nameWithType>) 來建立動態組件。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[組件內容](../../../docs/framework/app-domains/assembly-contents.md)|描述構成組件的項目。|  
|[組件資訊清單](../../../docs/framework/app-domains/assembly-manifest.md)|描述組件資訊清單中的資料，以及這些資料在組件中的儲存方式。|  
|[全域組件快取](../../../docs/framework/app-domains/gac.md)|描述全域組件快取，以及如何搭配組件使用。|  
|[強式名稱的組件](../../../docs/framework/app-domains/strong-named-assemblies.md)|描述強式名稱的組件之特性。|  
|[組件安全性考量](../../../docs/framework/app-domains/assembly-security-considerations.md)|討論組件安全性的運作方式。|  
|[組件版本控制](../../../docs/framework/app-domains/assembly-versioning.md)|提供 .NET Framework 版本控制原則的概觀。|  
|[組件定位](../../../docs/framework/app-domains/assembly-placement.md)|討論組件的位置。|  
|[組件和並存執行](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)|提供同時使用執行階段或組件之多個版本的概觀。|  
|[使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)|描述如何建立和簽署組件，以及如何設定組件屬性。|  
|[發出動態方法和組件](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|描述如何建立動態組件。|  
|[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|描述 .NET Framework 如何在執行階段中解析組件參考。|  
  
## <a name="reference"></a>參考資料  
 <xref:System.Reflection.Assembly?displayProperty=nameWithType>
