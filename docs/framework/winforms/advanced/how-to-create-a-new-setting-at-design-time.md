---
title: "如何：在設計階段建立新設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e8a05b6f37f7686f18a6200e009aabe7eed5537
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="8244d-102">如何：在設計階段建立新設定</span><span class="sxs-lookup"><span data-stu-id="8244d-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="8244d-103">您可以使用 設定設計工具，在設計階段建立新的設定。</span><span class="sxs-lookup"><span data-stu-id="8244d-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="8244d-104">設定設計工具是格線樣式介面，可讓您建立新的設定，並指定這些設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="8244d-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="8244d-105">您必須指定名稱、 值、 類型和您的新設定的範圍。</span><span class="sxs-lookup"><span data-stu-id="8244d-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="8244d-106">一旦建立的設定時，就是在程式碼中存取。</span><span class="sxs-lookup"><span data-stu-id="8244d-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="8244d-107">若要在 C# 中的設計階段建立新的設定</span><span class="sxs-lookup"><span data-stu-id="8244d-107">To create a new setting at design time in C#</span></span>  
  
1.  <span data-ttu-id="8244d-108">在**方案總管 中**，依序展開**屬性**您的專案節點。</span><span class="sxs-lookup"><span data-stu-id="8244d-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="8244d-109">按兩下您要加入新的設定.settings 檔案。</span><span class="sxs-lookup"><span data-stu-id="8244d-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="8244d-110">這個檔案的預設名稱是 Settings.settings。</span><span class="sxs-lookup"><span data-stu-id="8244d-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="8244d-111">在 設定設計工具中，設定名稱、 值、 類型和您的設定範圍。</span><span class="sxs-lookup"><span data-stu-id="8244d-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="8244d-112">每個資料列都代表單一的設定。</span><span class="sxs-lookup"><span data-stu-id="8244d-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="8244d-113">若要在 Visual Basic 中的設計階段建立新的設定</span><span class="sxs-lookup"><span data-stu-id="8244d-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="8244d-114">在**方案總管] 中**，以滑鼠右鍵按一下您的專案節點，然後選擇 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8244d-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="8244d-115">在**屬性**頁面上，選取**設定** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8244d-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="8244d-116">在 設定設計工具中，設定名稱、 值、 類型和您的設定範圍。</span><span class="sxs-lookup"><span data-stu-id="8244d-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="8244d-117">每個資料列都代表單一的設定。</span><span class="sxs-lookup"><span data-stu-id="8244d-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8244d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8244d-118">See Also</span></span>  
 [<span data-ttu-id="8244d-119">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="8244d-119">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="8244d-120">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="8244d-120">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="8244d-121">操作說明：在設計階段變更現有設定的值</span><span class="sxs-lookup"><span data-stu-id="8244d-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
