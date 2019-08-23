---
title: 多重文件介面 (MDI) 應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 23e0275d5e6b081ec02d669a78e8695453360637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956551"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="12556-102">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="12556-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="12556-103">多重文件介面 (MDI) 應用程式可讓您同時顯示多份檔, 每份檔都會顯示在自己的視窗中。</span><span class="sxs-lookup"><span data-stu-id="12556-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="12556-104">MDI 應用程式通常會有一個視窗功能表項目, 其中包含可在視窗或檔之間切換的子功能表。</span><span class="sxs-lookup"><span data-stu-id="12556-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12556-105">Windows Forms 中的 MDI 表單和單一檔介面 (SDI) 視窗之間有一些行為差異。</span><span class="sxs-lookup"><span data-stu-id="12556-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="12556-106">`Opacity`屬性不會影響 MDI 子表單的外觀。</span><span class="sxs-lookup"><span data-stu-id="12556-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="12556-107">此外, <xref:System.Windows.Forms.Form.CenterToParent%2A>方法不會影響 MDI 子表單的行為。</span><span class="sxs-lookup"><span data-stu-id="12556-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12556-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="12556-108">In This Section</span></span>  
 [<span data-ttu-id="12556-109">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="12556-109">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="12556-110">說明如何在 MDI 應用程式中建立多個檔的容器。</span><span class="sxs-lookup"><span data-stu-id="12556-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="12556-111">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="12556-111">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="12556-112">說明如何建立在 MDI 父表單中操作的一或多個視窗。</span><span class="sxs-lookup"><span data-stu-id="12556-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="12556-113">如何：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="12556-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="12556-114">提供驗證具有焦點之子視窗的指示 (並將其內容傳送至剪貼簿)。</span><span class="sxs-lookup"><span data-stu-id="12556-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="12556-115">如何：將資料傳送至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="12556-115">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="12556-116">提供將資訊傳輸至作用中子視窗的指示。</span><span class="sxs-lookup"><span data-stu-id="12556-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="12556-117">如何：排列 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="12556-117">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="12556-118">提供如何並排、串聯或排列 MDI 應用程式之子視窗的指示。</span><span class="sxs-lookup"><span data-stu-id="12556-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
