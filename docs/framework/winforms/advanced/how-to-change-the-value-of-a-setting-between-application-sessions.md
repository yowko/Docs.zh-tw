---
title: 如何：變更應用程式工作階段之間的設定值
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 475e57e8bfdd5f3296c6af0fb20a472c729ea75c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540711"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="59e51-102">如何：變更應用程式工作階段之間的設定值</span><span class="sxs-lookup"><span data-stu-id="59e51-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="59e51-103">有些時候，您可能要變更設定，以編譯及部署應用程式之後的應用程式工作階段之間的值。</span><span class="sxs-lookup"><span data-stu-id="59e51-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="59e51-104">例如，您可能要變更連接字串以指向正確的資料庫位置。</span><span class="sxs-lookup"><span data-stu-id="59e51-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="59e51-105">由於編譯及部署應用程式之後，都無法使用設計階段工具，您必須變更設定值，以手動方式在檔案中。</span><span class="sxs-lookup"><span data-stu-id="59e51-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="59e51-106">若要變更應用程式工作階段之間的設定值</span><span class="sxs-lookup"><span data-stu-id="59e51-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="59e51-107">使用 Microsoft 記事本或一些其他文字編輯器或 XML 編輯器，開啟您的應用程式相關聯.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="59e51-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="59e51-108">找出您想要變更設定的項目。</span><span class="sxs-lookup"><span data-stu-id="59e51-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="59e51-109">它看起來應該類似下列的範例。</span><span class="sxs-lookup"><span data-stu-id="59e51-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="59e51-110">輸入您設定的新值，然後儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="59e51-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59e51-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59e51-111">See also</span></span>
- [<span data-ttu-id="59e51-112">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="59e51-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [<span data-ttu-id="59e51-113">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="59e51-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
