---
title: 如何：在設計階段建立新設定
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 618355948578bd8f15e8cf7bec6f599e3169b77a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523763"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="c4488-102">如何：在設計階段建立新設定</span><span class="sxs-lookup"><span data-stu-id="c4488-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="c4488-103">您可以使用 設定設計工具，在設計階段建立新的設定。</span><span class="sxs-lookup"><span data-stu-id="c4488-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="c4488-104">設定設計工具是格線樣式介面，可讓您建立新的設定，並指定這些設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="c4488-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="c4488-105">您必須指定名稱、 值、 類型和您的新設定的範圍。</span><span class="sxs-lookup"><span data-stu-id="c4488-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="c4488-106">一旦建立的設定時，就是在程式碼中存取。</span><span class="sxs-lookup"><span data-stu-id="c4488-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="c4488-107">若要在 C# 中的設計階段建立新的設定</span><span class="sxs-lookup"><span data-stu-id="c4488-107">To create a new setting at design time in C#</span></span>  
  
1.  <span data-ttu-id="c4488-108">在**方案總管 中**，依序展開**屬性**您的專案節點。</span><span class="sxs-lookup"><span data-stu-id="c4488-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="c4488-109">按兩下您要加入新的設定.settings 檔案。</span><span class="sxs-lookup"><span data-stu-id="c4488-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="c4488-110">這個檔案的預設名稱是 Settings.settings。</span><span class="sxs-lookup"><span data-stu-id="c4488-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="c4488-111">在 設定設計工具中，設定名稱、 值、 類型和您的設定範圍。</span><span class="sxs-lookup"><span data-stu-id="c4488-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="c4488-112">每個資料列都代表單一的設定。</span><span class="sxs-lookup"><span data-stu-id="c4488-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="c4488-113">若要在 Visual Basic 中的設計階段建立新的設定</span><span class="sxs-lookup"><span data-stu-id="c4488-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="c4488-114">在**方案總管] 中**，以滑鼠右鍵按一下您的專案節點，然後選擇 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c4488-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="c4488-115">在**屬性**頁面上，選取**設定** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c4488-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="c4488-116">在 設定設計工具中，設定名稱、 值、 類型和您的設定範圍。</span><span class="sxs-lookup"><span data-stu-id="c4488-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="c4488-117">每個資料列都代表單一的設定。</span><span class="sxs-lookup"><span data-stu-id="c4488-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4488-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4488-118">See Also</span></span>  
 [<span data-ttu-id="c4488-119">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="c4488-119">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="c4488-120">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="c4488-120">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="c4488-121">操作說明：在設計階段變更現有設定的值</span><span class="sxs-lookup"><span data-stu-id="c4488-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
