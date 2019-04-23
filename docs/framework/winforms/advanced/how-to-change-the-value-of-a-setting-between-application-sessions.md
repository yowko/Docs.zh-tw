---
title: 如何：變更應用程式工作階段之間的設定值
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 95e613cb280813cd75d887d3cf147d7c897bc2e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318883"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>如何：變更應用程式工作階段之間的設定值
有些時候，您可能要變更設定，以編譯及部署應用程式之後的應用程式工作階段之間的值。 例如，您可能要變更連接字串以指向正確的資料庫位置。 由於編譯及部署應用程式之後，都無法使用設計階段工具，您必須變更設定值，以手動方式在檔案中。  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>若要變更應用程式工作階段之間的設定值  
  
1. 使用 Microsoft 記事本或一些其他文字編輯器或 XML 編輯器，開啟您的應用程式相關聯.config 檔案。  
  
2. 找出您想要變更設定的項目。 它看起來應該類似下列的範例。  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3. 輸入您設定的新值，然後儲存檔案。  
  
## <a name="see-also"></a>另請參閱

- [使用應用程式設定和使用者設定](using-application-settings-and-user-settings.md)
- [應用程式設定概觀](application-settings-overview.md)
