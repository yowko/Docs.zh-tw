---
title: 組件定位
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9b8357be5b9f49569114cbc1c2942eea03696eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180176"
---
# <a name="assembly-placement"></a>組件定位
對於大部分 .NET Framework 應用程式，您可以將構成該應用程式的組件放置在應用程式的目錄、應用程式目錄的子目錄或全域組件快取 (如果該組件是共用的) 中。 您可以使用組態檔中的 [\<codeBase> 項目](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)來覆寫 Common Language Runtime 尋找組件的位置。 如果組件不具有強式名稱，就會將使用 [\<codeBase> 項目](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)所指定的位置限制為應用程式目錄或子目錄。 如果組件具有強式名稱，[\<codeBase> 項目](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)即可以指定電腦或網路上的任何位置。  
  
 使用 Unmanaged 程式碼或 COM Interop 應用程式時，可套用類似的規則來尋找組件：如果將會有多個應用程式共用這個組件，應該將它安裝在全域組件快取中。 配合 Unmanaged 程式碼使用的組件必須匯出為型別程式庫並且加以註冊。 COM Interop 所使用的組件必須在資料庫目錄 (Catalog) 中註冊，不過在某些狀況下這項註冊會自動進行。  
  
## <a name="see-also"></a>另請參閱

- [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [設定應用程式](../../../docs/framework/configure-apps/index.md)
- [與非受控程式碼交互操作](../../../docs/framework/interop/index.md)
- [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
