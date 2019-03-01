---
title: 如何：將多組設定新增至您的應用程式C#
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 447d171cf9dbe2672ae138e9e902cbd72a206c94
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969632"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>如何：將多組設定新增至您在 C 中的應用程式\#
在某些情況下，您可能想要的應用程式中有多組設定。 比方說，如果您正在開發應用程式特定群組的設定應該在其中經常變更，它可能是個明智的選擇，讓檔案可以全面，取代成單一檔案的所有分隔它們保留其他設定不會受到影響。 Visual Studio 可讓您將多組設定新增至您的專案。 可透過 Properties.Settings 物件存取設定的其他集合。  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>若要將一組額外的設定新增至您的應用程式  
  
1.  從 [專案] 功能表選擇 [新增項目]。 [新增項目] 對話方塊隨即開啟。  
  
2.  在 **加入新項目**對話方塊中，選取**設定檔**，輸入檔案名稱，然後按一下**新增**將新的設定檔新增至您的解決方案。  
  
3.  在 **方案總管**，將拖曳至新的設定檔**屬性**資料夾。 這可讓您可在程式碼中使用的新設定。  
  
4.  新增並使用此檔案中的設定，就如同任何其他的設定檔。 您可以存取此設定，透過 Properties.Settings 物件群組。  
  
## <a name="see-also"></a>另請參閱
- [使用應用程式設定和使用者設定](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
