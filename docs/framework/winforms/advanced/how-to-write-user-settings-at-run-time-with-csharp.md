---
title: "如何：在執行階段使用 C# 撰寫使用者設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5966aef77c994d2657bd282ad15e8f59a64eeb47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="f0cbe-102">如何：在執行階段使用 C# 撰寫使用者設定</span><span class="sxs-lookup"><span data-stu-id="f0cbe-102">How To: Write User Settings at Run Time with C#</span></span> #
<span data-ttu-id="f0cbe-103">應用程式範圍的設定是唯讀的，並只能在設計階段變更，或藉由更改應用程式工作階段之間的 .config 檔案變更。</span><span class="sxs-lookup"><span data-stu-id="f0cbe-103">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="f0cbe-104">不過，使用者範圍的設定可以在執行階段撰寫，就如同您變更任何屬性值一樣。</span><span class="sxs-lookup"><span data-stu-id="f0cbe-104">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="f0cbe-105">新的值在應用程式工作階段期間保存。</span><span class="sxs-lookup"><span data-stu-id="f0cbe-105">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="f0cbe-106">您可以藉由呼叫 Save 方法在應用程式工作階段之間保存設定的變更。</span><span class="sxs-lookup"><span data-stu-id="f0cbe-106">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="f0cbe-107">如何：在執行階段使用 C# 撰寫和保存使用者設定</span><span class="sxs-lookup"><span data-stu-id="f0cbe-107">How To: Write and Persist User Settings at Run Time with C#</span></span>  
  
1.  <span data-ttu-id="f0cbe-108">存取設定，並指派新值，如本範例所示：</span><span class="sxs-lookup"><span data-stu-id="f0cbe-108">Access the setting and assign it a new value as shown in this example:</span></span>  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  <span data-ttu-id="f0cbe-109">如果您想要在應用程式工作階段之間保存變更的設定，請呼叫 Save 方法，如本範例所示：</span><span class="sxs-lookup"><span data-stu-id="f0cbe-109">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     <span data-ttu-id="f0cbe-110">使用者設定會儲存在使用者的本機隱藏應用程式儲存資料夾的子資料夾內。</span><span class="sxs-lookup"><span data-stu-id="f0cbe-110">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0cbe-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0cbe-111">See Also</span></span>  
 [<span data-ttu-id="f0cbe-112">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="f0cbe-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="f0cbe-113">操作說明：在執行階段使用 C# 讀取設定</span><span class="sxs-lookup"><span data-stu-id="f0cbe-113">How To: Read Settings at Run Time With C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="f0cbe-114">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="f0cbe-114">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
