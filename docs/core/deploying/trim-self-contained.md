---
title: 修剪獨立的應用程式
description: 瞭解如何修剪獨立的應用程式，以縮減其大小。 .NET Core 會將執行時間與獨立發行的應用程式組合，而且通常會包含更多執行時間，因此是必要的。
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: 7a4731e2cbaa3835e6aa6ba558dfa8cd03828e01
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053103"
---
# <a name="trim-self-contained-deployments-and-executables"></a>修剪獨立式部署及可執行檔

從 .NET 開始， [framework 相依的部署模型](index.md#publish-framework-dependent) 是最成功的部署模型。 在此案例中，應用程式開發人員只會將應用程式和協力廠商元件組合在一起，並預期在用戶端電腦上可以使用 .NET 執行時間和架構程式庫。 此部署模型也會繼續成為 .NET Core 中的主應用程式，但在某些情況下，framework 相依的模型不是最佳的。 替代方式是發佈獨立式 [應用程式](index.md#publish-self-contained)，其中 .net Core 執行時間和架構會與應用程式和協力廠商元件一起配套。

Trim 獨立部署模型是獨立部署模型的特製化版本，已優化以減少部署大小。 將部署大小降至最低是某些用戶端案例的重要需求，例如 Blazor 應用程式。 視應用程式的複雜度而定，只會參考架構元件的子集，而每個元件內的程式碼子集都需要執行應用程式。 未使用的程式庫部分是不必要的，而且可以從封裝的應用程式中修剪。

但是，應用程式的組建時間分析可能會在執行時間造成失敗，因為無法可靠地分析各種有問題的程式碼模式 (主要是以反映使用) 為中心。 因為無法保證可靠性，所以會以預覽功能的形式提供此部署模型。

組建時間分析引擎會提供警告給程式碼模式的開發人員，這些模式是 problemmatic 來偵測需要的其他程式碼。 您可以使用屬性來標注程式碼，以告訴修剪器要包含的其他內容。 您可以使用 [來源](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md)產生器，將許多反映模式取代為組建階段程式碼。

應用程式的修剪模式是使用設定進行設定 `TrimMode` 。 預設值為 `copyused` ，並將參考的元件與應用程式配套。 此 `link` 值會與 Blazor WebAssembly 應用程式搭配使用，並在元件中修剪未使用的程式碼。 Trim 分析警告會提供無法進行完整相依性分析的程式碼模式相關資訊。 預設會隱藏這些警告，並可將旗標設為來開啟這些警告 `SuppressTrimAnalysisWarnings` `false` 。 如需可用之修剪選項的詳細資訊，請參閱 [修剪選項](trimming-options.md)。

> [!NOTE]
> 修剪是 .NET Core 3.1、5.0 中的實驗性功能， _僅_ 適用于獨立發行的應用程式。

## <a name="prevent-assemblies-from-being-trimmed"></a>防止元件遭到修剪

有些情況下，修剪功能將無法偵測到參考。 例如，當您的應用程式或應用程式所參考的程式庫在執行時間元件上使用反映時，不會直接參考該元件。 修剪不知道這些間接參考，而會將程式庫從已發行的資料夾中排除。

當程式碼透過反映間接參考元件時，您可以防止元件使用設定進行修剪 `<TrimmerRootAssembly>` 。 下列範例示範如何防止元件稱為「元件」進行 `System.Security` 修剪：

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a>修剪您的應用程式-CLI

使用 [dotnet publish](../tools/dotnet-publish.md) 命令修剪您的應用程式。 當您發佈應用程式時，請設定下列屬性：

- 發佈為特定執行時間的獨立應用程式： `-r win-x64`
- 啟用修剪： `/p:PublishTrimmed=true`

下列範例會將適用于 Windows 的應用程式發佈為獨立的應用程式，並修剪輸出。

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

下列範例會在積極的修剪模式中發佈應用程式，而元件中未使用的程式碼將會被修剪，並啟用修剪器警告。

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</PropertyGroup>
```

如需詳細資訊，請參閱 [使用 .NET Core CLI 發佈 .Net Core 應用程式](deploy-with-cli.md)。

## <a name="trim-your-app---visual-studio"></a>修剪您的應用程式-Visual Studio

Visual Studio 會建立可重複使用的發行設定檔，以控制您的應用程式發佈方式。

01. 在 [ **方案總管** ] 窗格中，以滑鼠右鍵按一下您要發行的專案。 選取 [ **發佈 ...**]。

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="使用醒目提示 [發佈] 選項的右鍵功能表方案總管。":::

    如果您還沒有發行設定檔，請遵循指示來建立一個設定檔，並選擇 [ **資料夾** 目標] 類型。

01. 選擇 [編輯]****。

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Visual studio 以編輯按鈕發行設定檔。":::

01. 在 [ **設定檔設定** ] 對話方塊中，設定下列選項：

    - 設定**獨立**的**部署模式**。
    - 將 **目標運行** 時間設定為您想要發佈的目標平臺。
    - **在 [預覽]) 中選取 [修剪未使用的元件 (**]。

    選擇 [ **儲存** ] 以儲存設定，並返回 [ **發佈** ] 對話方塊。

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="醒目提示具有部署模式、目標執行時間和修剪未使用元件選項的 [設定檔設定] 對話方塊。":::

01. 選擇 [ **發行** ] 以發行已修剪的應用程式。

如需詳細資訊，請參閱 [使用 Visual Studio 發佈 .Net Core 應用程式](deploy-with-vs.md)。

## <a name="trim-your-app---visual-studio-for-mac"></a>修剪您的應用程式-Visual Studio for Mac

Visual Studio for Mac 不會提供在發佈期間修剪應用程式的選項。 您必須遵循 [ [修剪您的應用程式-CLI](#trim-your-app---cli) ] 區段中的指示，手動發佈。 如需詳細資訊，請參閱 [使用 .NET Core CLI 發佈 .Net Core 應用程式](deploy-with-cli.md)。

## <a name="see-also"></a>另請參閱

- [.Net Core 應用程式部署](index.md)。
- [使用 .NET Core CLI 發佈 .Net Core 應用程式](deploy-with-cli.md)。
- [使用 Visual Studio 發佈 .Net Core 應用程式](deploy-with-vs.md)。
- [dotnet publish 命令](../tools/dotnet-publish.md)。
