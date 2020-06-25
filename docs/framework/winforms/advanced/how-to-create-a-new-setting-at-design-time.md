---
title: 如何：在設計階段建立新設定
description: 瞭解如何使用 Visual Studio 中的 [設定設計工具]，在設計階段建立新的 Windows Forms 設定。
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: ce37b42191999e29de2f2f7f7e7abfa0ec3f4d47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325844"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="d7bf7-103">如何：在設計階段建立新設定</span><span class="sxs-lookup"><span data-stu-id="d7bf7-103">How To: Create a new setting at design time</span></span>

<span data-ttu-id="d7bf7-104">您可以在設計階段使用 Visual Studio 中的 [設定設計工具] 來建立新的設定。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-104">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="d7bf7-105">[設定設計工具] 是格線樣式的介面，可讓您建立新的設定，並指定這些設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-105">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="d7bf7-106">您必須為新的設定指定 [名稱]、[值]、[類型] 和 [範圍]。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-106">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="d7bf7-107">一旦建立設定之後，就可以在程式碼中存取它。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-107">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="d7bf7-108">在設計階段于 C 中建立新的設定\#</span><span class="sxs-lookup"><span data-stu-id="d7bf7-108">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="d7bf7-109">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-109">Open Visual Studio.</span></span>

2. <span data-ttu-id="d7bf7-110">在**方案總管**中，展開專案的 [**屬性**] 節點。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-110">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="d7bf7-111">按兩下要在其中新增設定的設定檔案。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-111">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="d7bf7-112">這個檔案的預設名稱是 [設定]。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-112">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="d7bf7-113">在 [設定設計工具] 中，設定您設定的**名稱**、**值**、**類型**和**範圍**。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-113">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="d7bf7-114">每個資料列都代表一個設定。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-114">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="d7bf7-115">在設計階段于 Visual Basic 中建立新的設定</span><span class="sxs-lookup"><span data-stu-id="d7bf7-115">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="d7bf7-116">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-116">Open Visual Studio.</span></span>

2. <span data-ttu-id="d7bf7-117">在**方案總管**中，以滑鼠右鍵按一下您的專案節點，然後選擇 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-117">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="d7bf7-118">在 [**屬性**] 頁面中，選取 [**設定**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-118">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="d7bf7-119">在 [設定設計工具] 中，設定您設定的**名稱**、**值**、**類型**和**範圍**。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-119">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="d7bf7-120">每個資料列都代表一個設定。</span><span class="sxs-lookup"><span data-stu-id="d7bf7-120">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7bf7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7bf7-121">See also</span></span>

- [<span data-ttu-id="d7bf7-122">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="d7bf7-122">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="d7bf7-123">應用程式設定總覽</span><span class="sxs-lookup"><span data-stu-id="d7bf7-123">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="d7bf7-124">如何：在設計階段變更現有設定的值</span><span class="sxs-lookup"><span data-stu-id="d7bf7-124">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
