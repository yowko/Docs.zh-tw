---
title: 多重文件介面 (MDI) 應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0ce7c66946d03d566b21473711cb6b3315885236
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61952044"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="61b31-102">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="61b31-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="61b31-103">多重文件介面 (MDI) 應用程式可讓您在此同時顯示多份文件，與它自己的視窗中顯示每個文件。</span><span class="sxs-lookup"><span data-stu-id="61b31-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="61b31-104">MDI 應用程式通常會有視窗功能表項目具有子功能表的視窗或文件之間切換。</span><span class="sxs-lookup"><span data-stu-id="61b31-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61b31-105">有一些行為差異 MDI 表單和單一文件介面 (SDI) windows 在 Windows Form 中。</span><span class="sxs-lookup"><span data-stu-id="61b31-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="61b31-106">`Opacity`屬性不會影響 MDI 子表單的外觀。</span><span class="sxs-lookup"><span data-stu-id="61b31-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="61b31-107">此外，<xref:System.Windows.Forms.Form.CenterToParent%2A>方法不會影響行為的 MDI 子表單。</span><span class="sxs-lookup"><span data-stu-id="61b31-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61b31-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="61b31-108">In This Section</span></span>  
 [<span data-ttu-id="61b31-109">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="61b31-109">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="61b31-110">說明如何建立在 MDI 應用程式內的多份文件的容器。</span><span class="sxs-lookup"><span data-stu-id="61b31-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="61b31-111">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="61b31-111">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="61b31-112">說明如何建立 MDI 父表單內操作的一或多個視窗。</span><span class="sxs-lookup"><span data-stu-id="61b31-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="61b31-113">如何：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="61b31-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="61b31-114">說明如何驗證具有焦點的子視窗 （並將其內容傳送到剪貼簿）。</span><span class="sxs-lookup"><span data-stu-id="61b31-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="61b31-115">如何：將資料傳送至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="61b31-115">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="61b31-116">說明如何傳輸至作用中的子視窗的資訊。</span><span class="sxs-lookup"><span data-stu-id="61b31-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="61b31-117">如何：排列 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="61b31-117">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="61b31-118">說明如何以並排顯示、 重疊顯示、 或排列 MDI 應用程式的子視窗。</span><span class="sxs-lookup"><span data-stu-id="61b31-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
