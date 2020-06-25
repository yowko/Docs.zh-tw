---
title: 控制項
description: 瞭解如何新增和放置 Windows Form 控制項。 您也可以在設計工具中操作控制項，並撰寫程式碼，在執行時間動態加入控制項。
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls
- controls [Windows Forms]
- Windows Forms controls, about Windows Forms controls
ms.assetid: f050de8f-4ebd-4042-94b8-edf9a1dbd52a
ms.openlocfilehash: 9ca4a2a1205663ae0ff4537a58cc1991a15da5d8
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324036"
---
# <a name="windows-forms-controls"></a><span data-ttu-id="385c6-104">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="385c6-104">Windows Forms controls</span></span>

<span data-ttu-id="385c6-105">當您設計及修改 Windows Forms 應用程式的使用者介面時，您必須新增、對齊和調整控制項的位置。</span><span class="sxs-lookup"><span data-stu-id="385c6-105">As you design and modify the user interface of your Windows Forms applications, you will need to add, align, and position controls.</span></span> <span data-ttu-id="385c6-106">控制項是表單物件內所包含的物件。</span><span class="sxs-lookup"><span data-stu-id="385c6-106">Controls are objects that are contained within form objects.</span></span> <span data-ttu-id="385c6-107">每一種控制項都有自己適合特定用途的一組屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="385c6-107">Each type of control has its own set of properties, methods, and events that make it suitable for a particular purpose.</span></span> <span data-ttu-id="385c6-108">您可以在設計工具中操作控制項和撰寫程式碼以在執行階段以動態方式加入控制項。</span><span class="sxs-lookup"><span data-stu-id="385c6-108">You can manipulate controls in the designer and write code to add controls dynamically at run time.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="385c6-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="385c6-109">In this section</span></span>

<span data-ttu-id="385c6-110">[將控制項放在 Windows Forms](putting-controls-on-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="385c6-110">[Putting Controls on Windows Forms](putting-controls-on-windows-forms.md)</span></span>\
<span data-ttu-id="385c6-111">提供將控制項加入表單的相關連結。</span><span class="sxs-lookup"><span data-stu-id="385c6-111">Provides links related to putting controls on forms.</span></span>

<span data-ttu-id="385c6-112">[排列 Windows Forms 上的控制項](how-to-align-multiple-controls-on-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="385c6-112">[Arranging Controls on Windows Forms](how-to-align-multiple-controls-on-windows-forms.md)</span></span>\
<span data-ttu-id="385c6-113">在表單上排列控制項的相關文章。</span><span class="sxs-lookup"><span data-stu-id="385c6-113">Articles related to arranging controls on forms.</span></span>

<span data-ttu-id="385c6-114">[標記個別 Windows Forms 控制項並提供其快捷方式](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)</span><span class="sxs-lookup"><span data-stu-id="385c6-114">[Labeling Individual Windows Forms Controls and Providing Shortcuts to Them](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)</span></span>\
<span data-ttu-id="385c6-115">描述控制項上的鍵盤快速鍵、文字標籤的用法以及輔助按鍵。</span><span class="sxs-lookup"><span data-stu-id="385c6-115">Describes the uses of keyboard shortcuts, text labels on controls, and modifier keys.</span></span>

<span data-ttu-id="385c6-116">[要在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="385c6-116">[Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md)</span></span>\
<span data-ttu-id="385c6-117">列出搭配 Windows Forms 使用的控制項，以及您可以使用每個控制項完成的基本作業。</span><span class="sxs-lookup"><span data-stu-id="385c6-117">Lists the controls that work with Windows Forms, and basic things you can accomplish with each control.</span></span>

<span data-ttu-id="385c6-118">[使用 .NET Framework 開發自訂 Windows Forms 控制項](developing-custom-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="385c6-118">[Developing Custom Windows Forms Controls with the .NET Framework](developing-custom-windows-forms-controls.md)</span></span>\
<span data-ttu-id="385c6-119">提供背景資訊和範例，以協助使用者開發自訂的 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="385c6-119">Provides background information and samples to help users develop custom Windows Forms controls.</span></span>

<span data-ttu-id="385c6-120">[在設計階段開發 Windows Forms 控制項](developing-windows-forms-controls-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="385c6-120">[Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md)</span></span>\
<span data-ttu-id="385c6-121">描述透過設計和繼承建立自訂控制項的技術。</span><span class="sxs-lookup"><span data-stu-id="385c6-121">Describes techniques for creating custom controls through design and inheritance.</span></span>

## <a name="related-sections"></a><span data-ttu-id="385c6-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="385c6-122">Related sections</span></span>

<span data-ttu-id="385c6-123">[用戶端應用程式](../../develop-client-apps.md)</span><span class="sxs-lookup"><span data-stu-id="385c6-123">[Client Applications](../../develop-client-apps.md)</span></span>\
<span data-ttu-id="385c6-124">提供開發 Windows 應用程式的概觀。</span><span class="sxs-lookup"><span data-stu-id="385c6-124">Provides an overview of developing Windows-based applications.</span></span>
