---
title: 針對 Visual Studio 2010 中的 .NET Framework 3.0 及 3.5 撰寫專案
ms.date: 03/30/2017
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
ms.openlocfilehash: 1469ce2906c1101bae4098cbcabd4a10a64c1c7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513815"
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a>針對 Visual Studio 2010 中的 .NET Framework 3.0 及 3.5 撰寫專案
您可以使用 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] 來建立以 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 3.0 或 3.5 版為目標的專案。 本主題描述如何執行這個工作。  
  
> [!NOTE]
>  當加入活動時，請務必設定所需的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 版本。 在加入活動之後變更工作流程的目標版本將會導致工作流程驗證失敗。  
  
> [!WARNING]
>  在 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] 中開啟擁有 .Net Framework 3.5 活動的現有工作流程將會導致 `this.SetValue()` 發生錯誤。 為了開啟之前使用舊版 .Net Framework 所建立的專案，請先在設計工具中開啟空白工作流程，然後加入 .Net Framework 3.5 活動。  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a>若要使用 Visual Studio 2010 建立 .NET Framework 3.0 或 3.5 專案  
  
1.  開啟 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。  
  
2.  選取**檔案**，**新**，**專案**。  
  
3.  在對話方塊上方的下拉式清單中，選取所需的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 版本。  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a>若要升級 .NET Framework 的目標版本  
  
1.  以滑鼠右鍵按一下方案總管 中的專案，然後選取**屬性**。  
  
2.  在**目標 Framework**下拉式清單中，選取所需的版本。
