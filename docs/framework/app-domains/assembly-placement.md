---
title: 組件定位
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 5eb7b5c35bb40d5a58390ccbd4619cbed4e06c52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119964"
---
# <a name="assembly-placement"></a>組件定位
對於大部分 .NET Framework 應用程式，您可以將構成該應用程式的組件放置在應用程式的目錄、應用程式目錄的子目錄或全域組件快取 (如果該組件是共用的) 中。 您可以使用設定檔中的[ \<程式碼基底> 元素](../configure-apps/file-schema/runtime/codebase-element.md)，覆寫 common language runtime 尋找元件的位置。 如果元件沒有強式名稱，則會將使用程式[ \<代碼基底> 元素](../configure-apps/file-schema/runtime/codebase-element.md)指定的位置限制為應用程式目錄或子目錄。 如果元件具有強式名稱，程式[ \<代碼基底> 元素](../configure-apps/file-schema/runtime/codebase-element.md)可以指定電腦或網路上的任何位置。  
  
 使用 Unmanaged 程式碼或 COM Interop 應用程式時，可套用類似的規則來尋找組件：如果將會有多個應用程式共用這個組件，應該將它安裝在全域組件快取中。 配合 Unmanaged 程式碼使用的組件必須匯出為型別程式庫並且加以註冊。 COM Interop 所使用的組件必須在資料庫目錄 (Catalog) 中註冊，不過在某些狀況下這項註冊會自動進行。  
  
## <a name="see-also"></a>另請參閱

- [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)
- [設定應用程式](../configure-apps/index.md)
- [與非受控程式碼交互操作](../interop/index.md)
- [.NET 中的組件](index.md)
