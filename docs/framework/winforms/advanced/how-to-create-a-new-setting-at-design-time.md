---
title: 如何：在設計階段建立新的設定
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 160d4a9f560479b3a66b2cf4d7712b24551fabee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558694"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="4861f-102">如何：在設計階段建立新的設定</span><span class="sxs-lookup"><span data-stu-id="4861f-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="4861f-103">您可以使用設定設計工具，在設計階段建立新的設定。</span><span class="sxs-lookup"><span data-stu-id="4861f-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="4861f-104">設定設計工具是可讓您建立新的設定，並指定這些設定的屬性方格樣式介面。</span><span class="sxs-lookup"><span data-stu-id="4861f-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="4861f-105">您必須指定名稱、 值、 類型和您的新設定的範圍。</span><span class="sxs-lookup"><span data-stu-id="4861f-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="4861f-106">一旦建立一項設定時，就可在程式碼中存取。</span><span class="sxs-lookup"><span data-stu-id="4861f-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="4861f-107">若要在設計階段中建立新的設定C#</span><span class="sxs-lookup"><span data-stu-id="4861f-107">To create a new setting at design time in C#</span></span>  
  
1.  <span data-ttu-id="4861f-108">在 **方案總管**，展開**屬性**在專案的節點。</span><span class="sxs-lookup"><span data-stu-id="4861f-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="4861f-109">按兩下您要在其中加入新的設定.settings 檔案。</span><span class="sxs-lookup"><span data-stu-id="4861f-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="4861f-110">此檔案的預設名稱是 Settings.settings。</span><span class="sxs-lookup"><span data-stu-id="4861f-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="4861f-111">在 設定設計工具中，設定名稱、 值、 類型和您的設定範圍。</span><span class="sxs-lookup"><span data-stu-id="4861f-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="4861f-112">每個資料列都代表單一設定。</span><span class="sxs-lookup"><span data-stu-id="4861f-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="4861f-113">若要在 Visual Basic 中的設計階段建立新的設定</span><span class="sxs-lookup"><span data-stu-id="4861f-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="4861f-114">在 **方案總管**，以滑鼠右鍵按一下您的專案節點，然後選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4861f-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="4861f-115">在 [**屬性**頁面上，選取**設定**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4861f-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="4861f-116">在 設定設計工具中，設定名稱、 值、 類型和您的設定範圍。</span><span class="sxs-lookup"><span data-stu-id="4861f-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="4861f-117">每個資料列都代表單一設定。</span><span class="sxs-lookup"><span data-stu-id="4861f-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4861f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4861f-118">See also</span></span>
- [<span data-ttu-id="4861f-119">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="4861f-119">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [<span data-ttu-id="4861f-120">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="4861f-120">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="4861f-121">如何：在設計階段的現有設定的值變更</span><span class="sxs-lookup"><span data-stu-id="4861f-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
