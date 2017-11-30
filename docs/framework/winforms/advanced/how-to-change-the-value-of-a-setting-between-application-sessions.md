---
title: "如何：變更應用程式工作階段之間的設定值"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dff90e499ce421f372137903daf34c09c21d5c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="29345-102">如何：變更應用程式工作階段之間的設定值</span><span class="sxs-lookup"><span data-stu-id="29345-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="29345-103">有時候，您可能想要變更應用程式工作階段之後編譯及部署應用程式之間的設定值。</span><span class="sxs-lookup"><span data-stu-id="29345-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="29345-104">例如，您可以變更連接字串，以指向正確的資料庫位置。</span><span class="sxs-lookup"><span data-stu-id="29345-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="29345-105">因為編譯和部署的應用程式後，就無法使用設計階段工具，您必須變更設定值，以手動方式在檔案中。</span><span class="sxs-lookup"><span data-stu-id="29345-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="29345-106">若要變更應用程式工作階段之間的設定值</span><span class="sxs-lookup"><span data-stu-id="29345-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="29345-107">使用 Microsoft 記事本或其他文字或 XML 編輯器，開啟您的應用程式相關聯.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="29345-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="29345-108">找出您想要變更設定的項目。</span><span class="sxs-lookup"><span data-stu-id="29345-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="29345-109">它看起來應該類似以下所顯示的範例。</span><span class="sxs-lookup"><span data-stu-id="29345-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="29345-110">輸入您設定的新值，然後儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="29345-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29345-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29345-111">See Also</span></span>  
 [<span data-ttu-id="29345-112">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="29345-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="29345-113">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="29345-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
