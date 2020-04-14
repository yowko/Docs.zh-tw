---
title: 可攜式類別庫的跨平台開發
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 7caddd7361b8f364762fb4357e35cb918ae99263
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242799"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>使用便攜式類庫進行跨平台開發

Visual Studio 中的便攜式類庫項目類型可説明您快速輕鬆地為 Microsoft 平臺構建跨平台應用和庫。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

可攜式類別庫可幫助您減少開發及測試程式碼的時間和成本。 使用此項目類型可以編寫和生成可移植的 .NET 框架程式集,然後從針對多個平臺(如 .NET Framework、iOS 或 Mac)的應用引用這些程式集。

即使在 Visual Studio 中建立可攜式類別庫專案並開始開發之後，您還是可以變更目標平台。 Visual Studio 使用新程式集編譯庫,這有助於標識需要在代碼中所做的更改。

## <a name="create-a-portable-class-library-project"></a>建立便攜式類別庫專案

要創建便攜式類庫,請使用可視化工作室中提供的範本。 創建新專案 (**檔案** > **新專案**),並在 **「新項目**」對話方塊中,選擇您的程式設計語言(可視化 C# 或可視化基本)。 然後,選擇**類庫(舊式可移植)** 範本。 輸入項目的名稱,然後選擇 **"確定**"。

將顯示「**新增便攜式類庫**」 對話框。 選擇兩個或多個目標,然後選擇 **「確定**」。

![在可視化工作室中添加攜帶型類庫目標](media/add-portable-class-library.png)

## <a name="change-targets"></a>變更目標

您可以在創建便攜式類庫專案時或開始開發後更改其目標平臺。 如果要在建立項目後更改目標,請在**解決方案資源管理員**中開啟可攜式類庫專案的快捷方式選單(不是解決方案),然後選擇**屬性**。 在項目屬性頁上,「**庫**」選項卡顯示專案當前目標的平臺。

![視覺化工作室中可攜式類庫的項目屬性](media/pcl-project-properties.png)

要新增或刪除目標,請選擇 **「更改」** 按鈕,然後選擇並清除相應的複選框。

當您變更目標時，可供您用來開發專案的 API 會變更，以配合您的選項。 Visual Studio 會提報因為目標變更而可能發生的錯誤和警告。

如果要在 Visual Studio 中進行更改之前評估程式集的可移植性,可以使用[.NET 可移植性分析器](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)。

## <a name="supported-types-and-members"></a>支援的類型和成員

可攜式類別庫專案中提供的類型和成員受到多個相容性因素所限制：

- 它們必須在您選取的目標之間共用。

- 它們必須在這些目標上具有類似的行為。

- 它們不能是要被取代的候選項。

- 它們在可攜式環境中必須是合理的，尤其是支援成員無法移植時。

如果可攜式類別庫和您選取的目標可支援某成員，該成員就會出現在 IntelliSense 的專案中。 不過，請記得，可攜式類別庫可能會支援 API，但您是否可以使用 API，取決於您選取的目標。

## <a name="api-differences-in-the-portable-class-library"></a>可攜式類別庫中的 API 差異

為了讓可攜式類別庫組件在所有支援的平台上都相容，可攜式類別庫中有部分成員已稍微變更。

## <a name="use-the-portable-class-library"></a>使用便攜式類別庫

建立可攜式類別庫專案之後，即可從其他專案參考該專案。 您可以參考此專案，或是包含您想要存取之類別的特定組件。

若要執行參考可攜式類別庫組件的應用程式，電腦上必須安裝目標平台所需的版本 (或以後版本)。 Visual Studio 包含所有必要架構，因此不需要進一步修改用來開發應用程式的電腦，即可執行該應用程式。

### <a name="deploy-a-universal-windows-app"></a>部署通用 Windows 應用

當您創建引用便攜式類庫程式集的通用 Windows 應用時,部署該應用所需的一切內容都包含在應用包中,並且不需要執行其他步驟。

### <a name="deploy-a-net-framework-app"></a>部署 .NET 架構套用

當您部署參考可攜式類別庫組件的 .NET Framework 應用程式時，必須指定正確 .NET Framework 版本的相依性。 藉由指定此相依性，您就可以確保所需的版本會隨著您的應用程式一起安裝。

- 要使用 ClickOnce 部署建立依賴項:在**解決方案資源管理器**中,選擇要發布的專案的專案節點。 (這是引用便攜式類庫專案的專案。在選單列上,選擇 **「項目** > **屬性**」,然後選擇「**發布**」選項卡。在 **「發布」** 頁上,選擇 **「先決條件**」。。 選取所需的 .NET Framework 版本做為必要條件。

- 要使用設置項目創建依賴項:在**解決方案資源管理員**中,選擇設置專案。 在功能表欄上,選擇 **「項目** > **屬性** > **先決條件**」。。 選取所需的 .NET Framework 版本做為必要條件。

有關部署 .NET 框架應用的詳細資訊,請參閱[開發人員的部署指南](../../../docs/framework/deployment/deployment-guide-for-developers.md)。

## <a name="see-also"></a>另請參閱

- [搭配 MVVM 使用可攜式類別庫](using-portable-class-library-with-model-view-view-model.md)
- [面向多個平台的庫的應用資源](app-resources-for-libraries-that-target-multiple-platforms.md)
- [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [部署](../../../docs/framework/deployment/net-framework-applications.md)
