---
title: 多重文件介面 (MDI) 應用程式
description: 瞭解如何 Windows Forms 多重文件介面 (MDI) 應用程式可讓您同時顯示多份檔，每份檔都會顯示在自己的視窗中。
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0912a989ac1710d72c9db1cceb0e695f0ca85dee
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174649"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="cb78c-103">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="cb78c-103">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="cb78c-104">多重文件介面 (MDI) 應用程式可讓您同時顯示多份檔，每份檔都會顯示在自己的視窗中。</span><span class="sxs-lookup"><span data-stu-id="cb78c-104">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="cb78c-105">MDI 應用程式通常會有一個視窗功能表項目，其中包含可在視窗或檔之間切換的子功能表。</span><span class="sxs-lookup"><span data-stu-id="cb78c-105">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb78c-106">在 Windows Forms 中，MDI 表單和單一檔介面 (SDI) 視窗之間有一些行為差異。</span><span class="sxs-lookup"><span data-stu-id="cb78c-106">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="cb78c-107">`Opacity`屬性不會影響 MDI 子表單的外觀。</span><span class="sxs-lookup"><span data-stu-id="cb78c-107">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="cb78c-108">此外， <xref:System.Windows.Forms.Form.CenterToParent%2A> 方法不會影響 MDI 子表單的行為。</span><span class="sxs-lookup"><span data-stu-id="cb78c-108">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb78c-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="cb78c-109">In This Section</span></span>  
 [<span data-ttu-id="cb78c-110">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="cb78c-110">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="cb78c-111">說明如何在 MDI 應用程式中建立多個檔的容器。</span><span class="sxs-lookup"><span data-stu-id="cb78c-111">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="cb78c-112">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="cb78c-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="cb78c-113">說明如何建立在 MDI 父表單中操作的一或多個視窗。</span><span class="sxs-lookup"><span data-stu-id="cb78c-113">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="cb78c-114">如何：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="cb78c-114">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="cb78c-115">說明如何驗證具有焦點 (的子視窗，並將其內容傳送至剪貼簿) 。</span><span class="sxs-lookup"><span data-stu-id="cb78c-115">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="cb78c-116">如何：傳送資料至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="cb78c-116">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="cb78c-117">提供將資訊傳輸至作用中子視窗的指示。</span><span class="sxs-lookup"><span data-stu-id="cb78c-117">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="cb78c-118">如何：安排 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="cb78c-118">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="cb78c-119">提供如何並排、串聯或排列 MDI 應用程式之子視窗的指示。</span><span class="sxs-lookup"><span data-stu-id="cb78c-119">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
