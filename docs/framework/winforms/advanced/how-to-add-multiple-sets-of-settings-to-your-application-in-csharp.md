---
title: 如何：在 C# 中將多組設定加入至應用程式
description: '瞭解如何使用 Visual Studio，在 c # 中將多組 Windows Forms 設定新增至您的應用程式。'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 579374ff101758b3224bc122c46b891280ed2609
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173441"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>如何：在 C 中將多組設定新增至您的應用程式\#

在某些情況下，您可能會想要在應用程式中有多組設定。 例如，如果您正在開發一個應用程式，其中特定的設定群組預期會經常變更，則將它們全部分隔成單一檔案可能會很明智，如此一來，就可以將檔案替換成批發，讓其他設定不受影響。 Visual Studio 可讓您將多組設定加入至專案。 您可以透過物件存取額外的設定集合 `Properties.Settings` 。

## <a name="add-an-additional-set-of-settings"></a>新增一組額外的設定

1. 在 Visual Studio 中，從 [**專案**] 功能表選擇 [**加入新專案**]。

   [新增項目]**** 對話方塊隨即開啟。

2. 在 [**加入新專案**] 對話方塊中，選取 [**設定檔**]，輸入檔案的名稱，然後按一下 [**新增**] 將新的設定檔新增至您的方案。

3. 在**方案總管**中，將新的設定檔案拖曳至 [ **Properties** ] 資料夾。 這可讓您在程式碼中使用新的設定。

4. 新增和使用此檔案中的設定，就像任何其他設定檔一樣。 您可以透過物件存取這組設定 `Properties.Settings` 。

## <a name="see-also"></a>另請參閱

- [使用應用程式設定和使用者設定](using-application-settings-and-user-settings.md)
- [應用程式設定總覽](application-settings-overview.md)
