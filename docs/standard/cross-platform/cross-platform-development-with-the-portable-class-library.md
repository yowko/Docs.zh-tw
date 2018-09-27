---
title: 可攜式類別庫的跨平台開發
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afaa8e118bb21e5c1e4f1c53b1d0d29ca6bb3bf5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47237263"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>使用可攜式類別庫的跨平台開發

在 Visual Studio 中的可攜式類別庫專案類型可協助您快速且輕鬆地建置跨平台應用程式和程式庫，針對 Microsoft 平台。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

可攜式類別庫可幫助您減少開發及測試程式碼的時間和成本。 撰寫及建置可攜式.NET Framework 組件，使用這種專案類型，並接著從.NET Framework、 iOS 或 mac 等的多個平台為目標的應用程式中參考這些組件

即使在 Visual Studio 中建立可攜式類別庫專案並開始開發之後，您還是可以變更目標平台。 Visual Studio 會編譯您的程式庫的新的組件，可協助您識別您需要在程式碼中進行的變更。

## <a name="create-a-portable-class-library-project"></a>建立可攜式類別庫專案

若要建立可攜式類別庫，請使用 Visual Studio 中提供的範本。 建立新的專案 (**檔案** > **新專案**)，然後在**新專案**對話方塊方塊中，選取您的程式語言 （Visual C# 或 Visual Basic）。 然後，選取**類別庫 （舊版可攜式）** 範本。 輸入您專案的名稱，然後選擇**確定**。

**加入可攜式類別庫** 對話方塊隨即出現。 選擇兩個或多個目標，然後選擇**確定**。

![Visual Studio 中加入可攜式類別程式庫的目標](media/add-portable-class-library.png)

## <a name="change-targets"></a>變更目標

當您在建立時，或您已經開始開發之後，您可以變更目標平台的可攜式類別庫專案。 如果您想要建立您的專案，在之後變更目標**方案總管**，開啟您的可攜式類別庫專案 （而非方案），捷徑功能表，然後選擇**屬性**. 在專案屬性頁面上，**程式庫** 索引標籤上顯示的平台專案的目前目標。

![在 Visual Studio 中的可攜式類別庫的專案屬性](media/pcl-project-properties.png)

若要新增或移除目標，選擇**變更**按鈕，然後選取及清除適當的核取方塊。

當您變更目標時，可供您用來開發專案的 API 會變更，以配合您的選項。 Visual Studio 會提報因為目標變更而可能發生的錯誤和警告。

如果您想要評估的可攜性的組件之前，請在 Visual Studio 中進行變更，您可以使用[.NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)。

## <a name="supported-types-and-members"></a>支援的類型和成員

可攜式類別庫專案中提供的類型和成員受到多個相容性因素所限制：

-   它們必須在您選取的目標之間共用。

-   它們必須在這些目標上具有類似的行為。

-   它們不能是要被取代的候選項。

-   它們在可攜式環境中必須是合理的，尤其是支援成員無法移植時。

如果可攜式類別庫和您選取的目標可支援某成員，該成員就會出現在 IntelliSense 的專案中。 不過，請記得，可攜式類別庫可能會支援 API，但您是否可以使用 API，取決於您選取的目標。

## <a name="api-differences-in-the-portable-class-library"></a>可攜式類別庫中的 API 差異

為了讓可攜式類別庫組件在所有支援的平台上都相容，可攜式類別庫中有部分成員已稍微變更。

## <a name="use-the-portable-class-library"></a>使用可攜式類別庫

建立可攜式類別庫專案之後，即可從其他專案參考該專案。 您可以參考此專案，或是包含您想要存取之類別的特定組件。

若要執行參考可攜式類別庫組件的應用程式，電腦上必須安裝目標平台所需的版本 (或以後版本)。 Visual Studio 包含所有必要架構，因此不需要進一步修改用來開發應用程式的電腦，即可執行該應用程式。

### <a name="deploy-a-universal-windows-app"></a>將通用 Windows 應用程式部署

當您建立通用 Windows 應用程式參考可攜式類別庫組件，您要部署應用程式的所有一切皆內含在應用程式套件中，並不需要任何進一步的步驟。

### <a name="deploy-a-net-framework-app"></a>部署.NET Framework 應用程式

當您部署參考可攜式類別庫組件的 .NET Framework 應用程式時，必須指定正確 .NET Framework 版本的相依性。 藉由指定此相依性，您就可以確保所需的版本會隨著您的應用程式一起安裝。

-   若要建立與 ClickOnce 部署的相依性： 在**方案總管 中**，選擇您想要發佈專案的專案節點。 (這是參考可攜式類別庫專案的專案。)在功能表列上選擇 **專案** > **屬性**，然後選擇**發佈** 索引標籤。在 **發佈**頁面上，選擇**必要條件**。 選取所需的 .NET Framework 版本做為必要條件。

-   若要建立與安裝專案的相依性： 在**方案總管] 中**，選擇 [安裝專案。 在功能表列上選擇 **專案** > **屬性** > **必要條件**。 選取所需的 .NET Framework 版本做為必要條件。

如需部署.NET Framework 應用程式的詳細資訊，請參閱 <<c0> [ 開發人員部署手冊](../../../docs/framework/deployment/deployment-guide-for-developers.md)。

## <a name="see-also"></a>另請參閱

- [搭配 MVVM 使用可攜式類別庫](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)
- [以多平台為目標之程式庫的應用程式資源](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)
- [.NET portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [部署](../../../docs/framework/deployment/net-framework-applications.md)
