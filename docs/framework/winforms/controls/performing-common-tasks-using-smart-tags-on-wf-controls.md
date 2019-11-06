---
title: 逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07fb43a711ae8b1e2e375b17b136c07f35b1cf39
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459582"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>逐步解說：使用智慧標籤執行一般工作

當您為 Windows Forms 應用程式建立表單和控制項時，您會重複執行許多工作。 以下是您將會遇到的一些經常執行的工作：

- 新增或移除 <xref:System.Windows.Forms.TabControl>上的索引標籤。

- 將控制項停駐于其父系。

- 變更 <xref:System.Windows.Forms.SplitContainer> 控制項的方向。

為了加速開發，許多控制項都提供智慧標籤，這些都是即時線上的功能表，可讓您在設計階段于單一手勢中執行像這些的一般工作。 這些工作稱為*智慧標籤動詞*。

智慧標籤會在設計工具中保持附加至控制項實例的存留期，而且一律可供使用。

## <a name="create-the-project"></a>建立專案

第一個步驟是建立專案並設定表單。

1. 在 Visual Studio 中，建立名為**SmartTagsExample**的 Windows 應用程式專案。

2. 在  **Windows Form 設計工具**中選取表單。

## <a name="use-smart-tags"></a>使用智慧標籤

在設計階段，智慧標籤在提供它們的控制項上一律可供使用。

1. 將 <xref:System.Windows.Forms.TabControl> 從 **工具箱** 拖曳至表單上。 請注意，出現在 <xref:System.Windows.Forms.TabControl>側邊的智慧標籤圖像（![智慧標籤圖像](./media/vs-winformsmttagglyph.gif)）。

2. 按一下智慧標籤圖像。 在出現在字元旁邊的快捷方式功能表中，選取 [**加入]** 索引標籤專案。 請注意，新的索引標籤頁已加入至 <xref:System.Windows.Forms.TabControl>。

3. 從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。

4. 按一下智慧標籤圖像。 在顯示于圖像的快捷方式功能表中，選取 [**加入資料行**] 專案。 請注意，新的資料行會加入至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。

5. 從 [工具箱] <xref:System.Windows.Forms.SplitContainer>**將** 控制項拖曳至表單。

6. 按一下智慧標籤圖像。 在顯示于圖像旁邊的快捷方式功能表中，選取**水準分隔器方向**專案。 請注意，<xref:System.Windows.Forms.SplitContainer> 控制項的分隔器列現在是水準方向。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
