---
title: 組件定位
description: 請參閱目錄中的 .NET 元件放置指導方針（例如，在全域組件快取中，或在應用程式的目錄或子目錄中）。
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 3106f6f01229057725cbc2e8e689a4e2247f95e6
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104960"
---
# <a name="assembly-placement"></a>組件定位
對於大部分 .NET Framework 應用程式，您可以將構成該應用程式的組件放置在應用程式的目錄、應用程式目錄的子目錄或全域組件快取 (如果該組件是共用的) 中。 您可以使用配置[ \<codeBase> 檔中的專案，覆](../configure-apps/file-schema/runtime/codebase-element.md)寫 common language runtime 尋找元件的位置。 如果元件沒有強式名稱，則使用[ \<codeBase> 元素](../configure-apps/file-schema/runtime/codebase-element.md)指定的位置會限制為應用程式目錄或子目錄。 如果元件具有強式名稱， [ \<codeBase> 元素](../configure-apps/file-schema/runtime/codebase-element.md)可以指定電腦或網路上的任何位置。  
  
 使用 Unmanaged 程式碼或 COM Interop 應用程式時，可套用類似的規則來尋找組件：如果將會有多個應用程式共用這個組件，應該將它安裝在全域組件快取中。 配合 Unmanaged 程式碼使用的組件必須匯出為型別程式庫並且加以註冊。 COM Interop 所使用的組件必須在資料庫目錄 (Catalog) 中註冊，不過在某些狀況下這項註冊會自動進行。  
  
## <a name="see-also"></a>另請參閱

- [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)
- [設定應用程式](../configure-apps/index.md)
- [與非受控程式碼交互操作](../interop/index.md)
- [.NET 中的組件](index.md)
