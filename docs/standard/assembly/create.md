---
title: 建立組件
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 81fffb2b2e1d56d6068bf6f663a13fad6968a383
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740514"
---
# <a name="create-assemblies"></a>建立組件

您可以使用 IDE (例如 Visual Studio) 或 Windows SDK 所提供的編譯器與工具來建立單一檔案或多檔案組件。 最簡單的組件是單一檔案，其具有簡單名稱並載入到單一應用程式定義域。 這個組件無法供應用程式目錄外部的其他組件參考，而且不會進行版本檢查。 若要解除安裝構成組件的應用程式，您只需要刪除其所在的目錄。 對許多開發人員而言，具有這些功能的組件就是部署應用程式所需的項目。

您可以從數個程式碼模組和資源檔建立多檔案組件。 您也可以建立可供多個應用程式共用的組件。 共用組件必須有強式名稱，而且可以部署在全域組件快取中。

根據下列因素，將程式碼模組和資源群組成組件時，您會有數個選項：

- 版本控制

     應該具有相同版本資訊的群組模組。

- 部署

     支援您部署模型的群組程式碼模組和資源。

- 重複使用

     可透過邏輯方式一起用於某個目的的群組模組。 例如，包含不常用於程式維護之類型和類別的組件可以放在相同的組件中。 此外，您想要與多個應用程式共用的類型應該群組為組件，並且應該使用強式名稱來簽署組件。

- 安全性

     包含需要相同安全性權限之類型的群組模組。

- 範圍

     包含其可視性應該限制為相同組件之類型的群組模組。

使通用語言運行時程式集可供非託管 COM 應用程式使用時，有特殊注意事項。 有關使用非託管代碼的詳細資訊，請參閱[向 COM 公開 .NET 框架元件](../../framework/interop/exposing-dotnet-components-to-com.md)。

## <a name="see-also"></a>另請參閱

- [組件版本控制](versioning.md)
- [如何：構建單檔程式集](../../framework/app-domains/build-single-file-assembly.md)
- [如何：構建多檔程式集](../../framework/app-domains/build-multifile-assembly.md)
- [運行時如何定位程式集](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [多檔案組件](../../framework/app-domains/multifile-assemblies.md)
