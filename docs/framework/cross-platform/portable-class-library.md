---
title: 可攜式類別庫的跨平台開發
description: 使用 .NET 中的便攜類別庫專案類型，快速且輕鬆地建立適用于 Microsoft 平臺的跨平臺應用程式和程式庫。
ms.date: 09/17/2018
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: ced595f62249609f4524d0b4b7bf734929619bfd
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687810"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>使用便攜類別庫進行跨平臺開發

Visual Studio 中的便攜類別庫專案類型可協助您快速且輕鬆地建立適用于 Microsoft 平臺的跨平臺應用程式和程式庫。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

可攜式類別庫可幫助您減少開發及測試程式碼的時間和成本。 使用此專案類型來撰寫及建立可移植的 .NET Framework 元件，然後從以多個平臺為目標的應用程式（例如 .NET Framework、iOS 或 Mac）參考這些元件。

即使在 Visual Studio 中建立可攜式類別庫專案並開始開發之後，您還是可以變更目標平台。 Visual Studio 使用新的元件來編譯您的程式庫，以協助您識別在程式碼中需要進行的變更。

## <a name="create-a-portable-class-library-project"></a>建立便攜類別庫專案

若要建立可移植的類別庫，請使用 Visual Studio 中提供的範本。 在 [新增專案] **(建立** 新專案  >  **New Project** ) ，然後在 [ **新增專案** ] 對話方塊中，選取您的程式設計語言 (Visual c # 或 Visual Basic) 。 然後，選取 **(舊版可移植) 範本的類別庫** 。 輸入專案的名稱，然後選擇 **[確定]** 。

[ **新增便攜類別庫** ] 對話方塊隨即出現。 選擇兩個或多個目標，然後選擇 **[確定]** 。

![在 Visual Studio 中新增便攜類別庫目標](media/add-portable-class-library.png)

## <a name="change-targets"></a>變更目標

您可以在建立便攜類別庫專案時，或在您開始開發之後，變更其目標平臺。 如果您想要在建立專案之後變更目標，請在 **方案總管** 中，開啟您的便攜類別庫專案的快捷方式功能表， (不是解決方案) ，然後選擇 [ **屬性** ]。 在 [專案屬性] 頁面上，[連結 **庫** ] 索引標籤會顯示您的專案目前的目標平臺。

![Visual Studio 中可移植類別庫的專案屬性](media/pcl-project-properties.png)

若要加入或移除目標，請選擇 [ **變更** ] 按鈕，然後選取並清除適當的核取方塊。

當您變更目標時，可供您用來開發專案的 API 會變更，以配合您的選項。 Visual Studio 會提報因為目標變更而可能發生的錯誤和警告。

如果您想要先評估元件的可攜性，然後再進行 Visual Studio 的變更，您可以使用 [.net 可攜性分析器](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)。

## <a name="supported-types-and-members"></a>支援的類型和成員

可攜式類別庫專案中提供的類型和成員受到多個相容性因素所限制：

- 它們必須在您選取的目標之間共用。

- 它們必須在這些目標上具有類似的行為。

- 它們不能是要被取代的候選項。

- 它們在可攜式環境中必須是合理的，尤其是支援成員無法移植時。

如果可攜式類別庫和您選取的目標可支援某成員，該成員就會出現在 IntelliSense 的專案中。 不過，請記得，可攜式類別庫可能會支援 API，但您是否可以使用 API，取決於您選取的目標。

## <a name="api-differences-in-the-portable-class-library"></a>可攜式類別庫中的 API 差異

為了讓可攜式類別庫組件在所有支援的平台上都相容，可攜式類別庫中有部分成員已稍微變更。

## <a name="use-the-portable-class-library"></a>使用可移植類別庫

建立可攜式類別庫專案之後，即可從其他專案參考該專案。 您可以參考此專案，或是包含您想要存取之類別的特定組件。

若要執行參考可攜式類別庫組件的應用程式，電腦上必須安裝目標平台所需的版本 (或以後版本)。 Visual Studio 包含所有必要架構，因此不需要進一步修改用來開發應用程式的電腦，即可執行該應用程式。

### <a name="deploy-a-universal-windows-app"></a>部署通用 Windows 應用程式

當您建立參考便攜類別庫元件的通用 Windows 應用程式時，部署應用程式所需的所有專案都會包含在應用程式套件中，而不需要採取進一步的步驟。

### <a name="deploy-a-net-framework-app"></a>部署 .NET Framework 應用程式

當您部署參考可攜式類別庫組件的 .NET Framework 應用程式時，必須指定正確 .NET Framework 版本的相依性。 藉由指定此相依性，您就可以確保所需的版本會隨著您的應用程式一起安裝。

- 若要建立與 ClickOnce 部署的相依性：在 [ **方案總管** 中，選擇您要發行之專案的專案節點。  (這是參考便攜類別庫專案的專案。 ) 在功能表列上，選擇 [ **專案**  >  **屬性** ]，然後選擇 [ **發行** ] 索引標籤。在 [ **發佈** ] 頁面上，選擇 [ **必要條件** ]。 選取所需的 .NET Framework 版本做為必要條件。

- 若要建立與安裝專案的相依性：在 [ **方案總管** 中，選擇安裝專案。 在功能表列上，選擇 [ **專案**  >  **屬性**  >  **必要條件** ]。 選取所需的 .NET Framework 版本做為必要條件。

如需部署 .NET Framework 應用程式的詳細資訊，請參閱 [開發人員的部署指南](../../framework/deployment/deployment-guide-for-developers.md)。

## <a name="see-also"></a>請參閱

- [搭配 MVVM 使用可攜式類別庫](using-portable-class-library-with-model-view-view-model.md)
- [以多個平臺為目標之程式庫的應用程式資源](app-resources-for-libraries-that-target-multiple-platforms.md)
- [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](support-for-windows-store-apps-and-windows-runtime.md)
- [部署](../../framework/deployment/net-framework-applications.md)
