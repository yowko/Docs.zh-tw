---
title: 建立元件
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2dda45cca182d75bc77916cdf862ada9faead9ec
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973303"
---
# <a name="create-assemblies"></a>建立元件

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

- 範圍設定

     包含其可視性應該限制為相同組件之類型的群組模組。

將 common language runtime 元件提供給未受管理的 COM 應用程式時，有一些特殊的考慮。 如需使用非受控碼的詳細資訊，請參閱[將 .NET Framework 元件公開給 COM](../../framework/interop/exposing-dotnet-components-to-com.md)。

## <a name="see-also"></a>另請參閱

- [具有元件的程式](program.md)
- [元件版本控制](versioning.md)
- [如何：建立單一檔案元件](../../framework/app-domains/build-single-file-assembly.md)
- [如何：建立多檔案元件](../../framework/app-domains/build-multifile-assembly.md)
- [執行階段如何找出組件](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [多檔案元件](../../framework/app-domains/multifile-assemblies.md)
