---
title: Windows Form 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls
- controls [Windows Forms]
- Windows Forms controls, about Windows Forms controls
ms.assetid: f050de8f-4ebd-4042-94b8-edf9a1dbd52a
ms.openlocfilehash: 1088781a7780df71773b01a3816f024562abfcaf
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986990"
---
# <a name="windows-forms-controls"></a><span data-ttu-id="8a995-102">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="8a995-102">Windows Forms controls</span></span>

<span data-ttu-id="8a995-103">當您設計及修改 Windows Forms 應用程式的使用者介面時，您必須新增、對齊和調整控制項的位置。</span><span class="sxs-lookup"><span data-stu-id="8a995-103">As you design and modify the user interface of your Windows Forms applications, you will need to add, align, and position controls.</span></span> <span data-ttu-id="8a995-104">控制項是表單物件內所包含的物件。</span><span class="sxs-lookup"><span data-stu-id="8a995-104">Controls are objects that are contained within form objects.</span></span> <span data-ttu-id="8a995-105">每一種控制項都有自己適合特定用途的一組屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="8a995-105">Each type of control has its own set of properties, methods, and events that make it suitable for a particular purpose.</span></span> <span data-ttu-id="8a995-106">您可以在設計工具中操作控制項和撰寫程式碼以在執行階段以動態方式加入控制項。</span><span class="sxs-lookup"><span data-stu-id="8a995-106">You can manipulate controls in the designer and write code to add controls dynamically at run time.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8a995-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="8a995-107">In this section</span></span>

<span data-ttu-id="8a995-108">[將控制項加入 Windows Forms](putting-controls-on-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="8a995-108">[Putting Controls on Windows Forms](putting-controls-on-windows-forms.md)</span></span>\
<span data-ttu-id="8a995-109">提供將控制項加入表單的相關連結。</span><span class="sxs-lookup"><span data-stu-id="8a995-109">Provides links related to putting controls on forms.</span></span>

<span data-ttu-id="8a995-110">[排列 Windows Forms 上的控制項](how-to-align-multiple-controls-on-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="8a995-110">[Arranging Controls on Windows Forms](how-to-align-multiple-controls-on-windows-forms.md)</span></span>\
<span data-ttu-id="8a995-111">在表單上排列控制項的相關文章。</span><span class="sxs-lookup"><span data-stu-id="8a995-111">Articles related to arranging controls on forms.</span></span>

<span data-ttu-id="8a995-112">[標記個別 Windows Forms 控制項並提供其快捷方式](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)</span><span class="sxs-lookup"><span data-stu-id="8a995-112">[Labeling Individual Windows Forms Controls and Providing Shortcuts to Them](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)</span></span>\
<span data-ttu-id="8a995-113">描述控制項上的鍵盤快速鍵、文字標籤的用法以及輔助按鍵。</span><span class="sxs-lookup"><span data-stu-id="8a995-113">Describes the uses of keyboard shortcuts, text labels on controls, and modifier keys.</span></span>

<span data-ttu-id="8a995-114">[要在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="8a995-114">[Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md)</span></span>\
<span data-ttu-id="8a995-115">列出搭配 Windows Forms 使用的控制項，以及您可以使用每個控制項完成的基本作業。</span><span class="sxs-lookup"><span data-stu-id="8a995-115">Lists the controls that work with Windows Forms, and basic things you can accomplish with each control.</span></span>

<span data-ttu-id="8a995-116">[使用 .NET Framework 開發自訂的 Windows Forms 控制項](developing-custom-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="8a995-116">[Developing Custom Windows Forms Controls with the .NET Framework](developing-custom-windows-forms-controls.md)</span></span>\
<span data-ttu-id="8a995-117">提供背景資訊和範例，以協助使用者開發自訂的 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="8a995-117">Provides background information and samples to help users develop custom Windows Forms controls.</span></span>

<span data-ttu-id="8a995-118">[在設計階段開發 Windows Forms 控制項](developing-windows-forms-controls-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="8a995-118">[Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md)</span></span>\
<span data-ttu-id="8a995-119">描述透過設計和繼承建立自訂控制項的技術。</span><span class="sxs-lookup"><span data-stu-id="8a995-119">Describes techniques for creating custom controls through design and inheritance.</span></span>

## <a name="related-sections"></a><span data-ttu-id="8a995-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="8a995-120">Related sections</span></span>

<span data-ttu-id="8a995-121">[用戶端應用程式](../../develop-client-apps.md)</span><span class="sxs-lookup"><span data-stu-id="8a995-121">[Client Applications](../../develop-client-apps.md)</span></span>\
<span data-ttu-id="8a995-122">提供開發 Windows 應用程式的概觀。</span><span class="sxs-lookup"><span data-stu-id="8a995-122">Provides an overview of developing Windows-based applications.</span></span>
