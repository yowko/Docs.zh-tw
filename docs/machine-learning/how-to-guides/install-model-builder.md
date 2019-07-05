---
title: 如何安裝模型建立器
description: 了解如何安裝 ML.NET 模型建立器工具
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 54ab595c56f816517180aab48022c7df207fe84d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410566"
---
# <a name="how-to-install-mlnet-model-builder"></a>了解如何安裝 ML.NET 模型建立器

了解如何安裝 ML.NET 模型建立器，將機器學習服務新增至您的 .NET 應用程式。

> [!NOTE]
> 模型建立器目前為預覽版。

## <a name="pre-requisites"></a>必要條件

- Visual Studio 2017 15.9.12 或更新版本 / Visual Studio 2019
- .NET Core 2.1 或更新版本的 SDK

## <a name="limitations"></a>限制

- ML.NET 模型建立器延伸模組目前僅適用於 Windows 的 Visual Studio。
- 1 GB 的定型資料集限制
- SQL Server 的定型上限為 10 萬筆資料列
- 不支援 Microsoft SQL Server Data Tools for Visual Studio 2017

## <a name="install"></a>安裝

您可透過 Visual Studio Marketplace，或從 Visual Studio 安裝 ML.NET 模型建立器。 

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

1. 從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07) 下載
1. 遵循提示安裝到個別的 Visual Studio 版本

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. 在功能表列上，選取 [工具]   > [延伸模組和更新] 
1. 在 [延伸模組和更新]  提示內部，選取「線上」  節點。
1. 在搜尋列中，搜尋「ML.NET 模型建立器」  ，然後從結果中選取 ML.NET 模型建立器 (預覽)
1. 遵循提示完成安裝

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. 在功能表列上，選取 [延伸模組]   > [管理延伸模組] 
1. 在 [延伸模組和更新]  提示內部，選取「線上」  節點。
1. 在搜尋列中鍵入「ML.NET 模型建立器」  ，選取 ML.NET 模型建立器 (預覽)
1. 遵循提示完成安裝

## <a name="uninstall"></a>解除安裝

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. 在功能表列上，選取 [工具]   > [延伸模組和更新] 
1. 在 [延伸模組和更新]  提示內部，展開「已安裝的」  節點，然後選取 [工具] 
1. 從工具清單選取 ML.NET 模型建立器 (預覽)，然後選取 [解除安裝] 
1. 遵循提示完成解除安裝。

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. 在功能表列上，選取 [延伸模組]   > [管理延伸模組] 
1. 在 [延伸模組和更新]  提示內部，展開「已安裝的」  節點，然後選取 [工具] 
1. 從工具清單選取 ML.NET 模型建立器 (預覽)，然後選取 [解除安裝] 
1. 遵循提示完成解除安裝。

## <a name="upgrade"></a>升級

升級程序類似安裝程序。 從 Visual Studio Marketplace 或使用 Visual Studio 的延伸模組管理員下載最新版本。
