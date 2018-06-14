---
title: 如何：變更應用程式工作階段之間的設定值
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 383f72f223fb92170d16a9538c94e67825009abb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523406"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>如何：變更應用程式工作階段之間的設定值
有時候，您可能想要變更應用程式工作階段之後編譯及部署應用程式之間的設定值。 例如，您可以變更連接字串，以指向正確的資料庫位置。 因為編譯和部署的應用程式後，就無法使用設計階段工具，您必須變更設定值，以手動方式在檔案中。  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>若要變更應用程式工作階段之間的設定值  
  
1.  使用 Microsoft 記事本或其他文字或 XML 編輯器，開啟您的應用程式相關聯.config 檔案。  
  
2.  找出您想要變更設定的項目。 它看起來應該類似以下所顯示的範例。  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  輸入您設定的新值，然後儲存檔案。  
  
## <a name="see-also"></a>另請參閱  
 [使用應用程式設定和使用者設定](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
