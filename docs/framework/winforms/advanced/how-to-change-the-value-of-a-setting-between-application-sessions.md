---
title: 如何：變更應用程式工作階段之間的設定值
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: c1626cea581e5c180665d0ce805dea3e67f27a05
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714355"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="094cf-102">如何：變更應用程式工作階段之間的設定值</span><span class="sxs-lookup"><span data-stu-id="094cf-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="094cf-103">有些時候，您可能要變更設定，以編譯及部署應用程式之後的應用程式工作階段之間的值。</span><span class="sxs-lookup"><span data-stu-id="094cf-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="094cf-104">例如，您可能要變更連接字串以指向正確的資料庫位置。</span><span class="sxs-lookup"><span data-stu-id="094cf-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="094cf-105">由於編譯及部署應用程式之後，都無法使用設計階段工具，您必須變更設定值，以手動方式在檔案中。</span><span class="sxs-lookup"><span data-stu-id="094cf-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="094cf-106">若要變更應用程式工作階段之間的設定值</span><span class="sxs-lookup"><span data-stu-id="094cf-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="094cf-107">使用 Microsoft 記事本或一些其他文字編輯器或 XML 編輯器，開啟您的應用程式相關聯.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="094cf-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="094cf-108">找出您想要變更設定的項目。</span><span class="sxs-lookup"><span data-stu-id="094cf-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="094cf-109">它看起來應該類似下列的範例。</span><span class="sxs-lookup"><span data-stu-id="094cf-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="094cf-110">輸入您設定的新值，然後儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="094cf-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="094cf-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="094cf-111">See also</span></span>
- [<span data-ttu-id="094cf-112">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="094cf-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="094cf-113">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="094cf-113">Application Settings Overview</span></span>](application-settings-overview.md)
