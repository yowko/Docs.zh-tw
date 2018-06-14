---
title: 如何：在 C# 中將多組設定加入至應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 029dffc878c62613e291620a2bd86971f369d15a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520805"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>如何：在 C# 中將多組設定加入至應用程式 #
在某些情況下，您可以在應用程式中有多組設定。 比方說，如果您開發的應用程式特定的設定群組打算經常變更，它可能是個明智的選擇，讓檔案可以批發，取代成單一檔案的所有分隔它們句子不受影響的其他設定。 Visual Studio 可讓您將多組設定加入至專案。 可透過 Properties.Settings 物件存取設定的其他設定。  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>將一組額外的設定新增至您的應用程式  
  
1.  從 [專案] 功能表選擇 [新增項目]。 [新增項目] 對話方塊隨即開啟。  
  
2.  在**加入新項目**對話方塊中，選取**設定檔**、 輸入檔案名稱，然後按一下**新增**將新的設定檔新增至您的方案。  
  
3.  在**方案總管 中**，拖曳至新的設定檔**屬性**資料夾。 這可讓您可在程式碼中使用新的設定。  
  
4.  加入並使用此檔案中的設定，就如同任何其他設定檔。 您可以存取此設定經由 Properties.Settings 物件群組。  
  
## <a name="see-also"></a>另請參閱  
 [使用應用程式設定和使用者設定](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
