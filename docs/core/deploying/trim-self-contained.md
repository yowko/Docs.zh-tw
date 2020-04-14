---
title: 修剪自包含應用程式
description: 瞭解如何修剪自包含應用以減小其大小。 .NET Core 將運行時與自包含發佈的應用捆綁在一起,並且通常包含更多運行時,因此有必要這樣做。
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bb8ac88c5e16b7fd20a7670e4ad76dbe4b44da1b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242896"
---
# <a name="trim-self-contained-deployments-and-executables"></a>修剪獨立式部署及可執行檔

發佈應用程式自包含時,.NET Core 運行時與應用程式捆綁在一起。 這種捆綁為打包的應用程式增加了大量內容。 在部署應用程式時,大小通常是一個重要因素。 保持包應用程式的大小盡可能小通常是應用程式開發人員的目標。

根據應用程式的複雜性,運行應用程式只需要運行時的子集。 這些未使用的運行時部分是不必要的,可以從打包的應用程式修剪。

修剪功能的工作原理是檢查應用程式二進位檔,以發現和生成所需運行時程式集的圖形。 排除未引用的剩餘運行時程式集。

> [!NOTE]
> 修剪是 .NET Core 3.1 中的實驗功能,_僅適用於_自包含發布的應用程式。

## <a name="prevent-assemblies-from-being-trimmed"></a>防止修剪裝配體

在某些情況下,修剪功能將無法檢測引用。 例如,當應用程式或應用程式引用的庫在運行時程式集上使用反射時,不會直接引用該程式集。 修剪不知道這些間接引用,並且會將庫從已發佈的資料夾中排除。

當代碼通過反射間接引用程式集時,可以防止使用`<TrimmerRootAssembly>`設置修剪程式集。 下面的範例簡報如何防止修剪`System.Security`稱為 程式集的程式集:

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a>修剪你的應用程式 - CLI

使用[dotnet 發佈](../tools/dotnet-publish.md)命令修剪應用程式。 發佈應用時,請設置以下三個設置:

- 以自包含身份發佈:`--self-contained true`
- 關閉單檔:`-p:PublishSingleFile=false`
- 開啟修剪:`p:PublishTrimmed=true`

下面的範例將 Windows 10 的應用發佈為自包含並修剪輸出。

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true -p:PublishSingleFile=false -p:PublishTrimmed=true
```

有關詳細資訊,請參閱發佈[.NET 核心應用 ,以及 .NET 核心 CLI](deploy-with-cli.md)。

## <a name="trim-your-app---visual-studio"></a>修剪你的應用程式 - 視覺工作室

Visual Studio 創建可重用的發佈配置檔,以控制應用程式的發佈方式。

01. 在 **「解決方案資源管理員」** 窗格中,右鍵單擊要發布的專案。 選擇 **"發佈..."**

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="解決方案資源管理器,右鍵單擊功能表突出顯示"發佈"選項。":::

    如果還沒有發佈設定檔,請按照說明創建一個設定檔,然後選擇 **「資料夾**目標類型」。

01. 選擇 [編輯]****。

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="可視化工作室發佈配置檔與編輯按鈕。":::

01. 在 **「設定檔設定」對話框**中,設定以下選項:

    - 將**部署模式**設定為**自包含**。
    - 將**目標運行時**設置為要發佈到的平臺。
    - 選擇 **「修剪未使用的裝配體(在預覽中)**

    選擇 **「儲存**」以儲存設定並傳回到 **「發布」** 對話方塊。

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="設定檔設定對話框,突出顯示了部署模式、目標運行時和修剪未使用的程式集選項。":::

01. 選擇 **「發布」** 以發佈已修剪的應用。

有關詳細資訊,請參閱發佈[.NET 核心應用與可視化工作室](deploy-with-vs.md)。

## <a name="trim-your-app---visual-studio-for-mac"></a>修剪你的應用程式 - Mac 的視覺化工作室

適用於 Mac 的可視化工作室不提供在發表期間修剪應用的選項。 您需要按照[「修剪應用 - CLI」](#trim-your-app---cli)部分的說明手動發佈。 有關詳細資訊,請參閱發佈[.NET 核心應用 ,以及 .NET 核心 CLI](deploy-with-cli.md)。

## <a name="see-also"></a>另請參閱

- [.NET 核心應用程式部署](index.md)。
- [使用 .NET 核心 CLI 發佈 .NET 核心應用程式](deploy-with-cli.md)。
- [發布 .NET 核心應用程式與視覺化工作室](deploy-with-vs.md)。
- [點網發佈命令](../tools/dotnet-publish.md).
