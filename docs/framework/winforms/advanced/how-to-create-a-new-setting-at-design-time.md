---
title: 如何：在設計階段建立新設定
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 35a7cd8cc1daaf76a25977751ddc9ec0709e5947
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037897"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="d06cb-102">如何：在設計階段建立新設定</span><span class="sxs-lookup"><span data-stu-id="d06cb-102">How To: Create a new setting at design time</span></span>

<span data-ttu-id="d06cb-103">您可以在設計階段使用 Visual Studio 中的 [設定設計工具] 來建立新的設定。</span><span class="sxs-lookup"><span data-stu-id="d06cb-103">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="d06cb-104">[設定設計工具] 是格線樣式的介面, 可讓您建立新的設定, 並指定這些設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="d06cb-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="d06cb-105">您必須為新的設定指定 [名稱]、[值]、[類型] 和 [範圍]。</span><span class="sxs-lookup"><span data-stu-id="d06cb-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="d06cb-106">一旦建立設定之後, 就可以在程式碼中存取它。</span><span class="sxs-lookup"><span data-stu-id="d06cb-106">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="d06cb-107">在設計階段于 C 中建立新的設定\#</span><span class="sxs-lookup"><span data-stu-id="d06cb-107">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="d06cb-108">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d06cb-108">Open Visual Studio.</span></span>

2. <span data-ttu-id="d06cb-109">在**方案總管**中, 展開專案的 [**屬性**] 節點。</span><span class="sxs-lookup"><span data-stu-id="d06cb-109">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="d06cb-110">按兩下要在其中新增設定的設定檔案。</span><span class="sxs-lookup"><span data-stu-id="d06cb-110">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="d06cb-111">這個檔案的預設名稱是 [設定]。</span><span class="sxs-lookup"><span data-stu-id="d06cb-111">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="d06cb-112">在 [設定設計工具] 中, 設定您設定的**名稱**、**值**、**類型**和**範圍**。</span><span class="sxs-lookup"><span data-stu-id="d06cb-112">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="d06cb-113">每個資料列都代表一個設定。</span><span class="sxs-lookup"><span data-stu-id="d06cb-113">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="d06cb-114">在設計階段于 Visual Basic 中建立新的設定</span><span class="sxs-lookup"><span data-stu-id="d06cb-114">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="d06cb-115">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d06cb-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="d06cb-116">在**方案總管**中, 以滑鼠右鍵按一下您的專案節點, 然後選擇 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="d06cb-116">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="d06cb-117">在 [**屬性**] 頁面中, 選取 [**設定**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d06cb-117">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="d06cb-118">在 [設定設計工具] 中, 設定您設定的**名稱**、**值**、**類型**和**範圍**。</span><span class="sxs-lookup"><span data-stu-id="d06cb-118">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="d06cb-119">每個資料列都代表一個設定。</span><span class="sxs-lookup"><span data-stu-id="d06cb-119">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="d06cb-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d06cb-120">See also</span></span>

- [<span data-ttu-id="d06cb-121">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="d06cb-121">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="d06cb-122">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="d06cb-122">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="d06cb-123">如何：在設計階段變更現有設定的值</span><span class="sxs-lookup"><span data-stu-id="d06cb-123">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
