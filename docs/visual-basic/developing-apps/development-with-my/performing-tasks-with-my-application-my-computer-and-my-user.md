---
title: "使用 My.Application、My.Computer 和 My.User 執行工作 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d55e0b3a126f2216d005c7bddbcaefb7d8f0a580
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="99fdb-102">使用 My.Application、My.Computer 和 My.User 執行工作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99fdb-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="99fdb-103">三個中央`My`物件提供存取資訊並經常搭配使用的功能是`My.Application`(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>)， `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)，和`My.User`(<xref:Microsoft.VisualBasic.ApplicationServices.User>)。</span><span class="sxs-lookup"><span data-stu-id="99fdb-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="99fdb-104">您可以使用這些物件，分別存取與目前的應用程式、，安裝應用程式的電腦或應用程式，目前使用者相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="99fdb-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="99fdb-105">My.Application、 My.Computer 和 My.User</span><span class="sxs-lookup"><span data-stu-id="99fdb-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="99fdb-106">下列範例示範資訊的可使用擷取`My`。</span><span class="sxs-lookup"><span data-stu-id="99fdb-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 <span data-ttu-id="99fdb-107">除了擷取資訊，透過這三個物件所公開的成員也可讓您執行該物件相關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="99fdb-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="99fdb-108">比方說，您可以存取各種不同的方法來操作檔案，或更新透過登錄`My.Computer`。</span><span class="sxs-lookup"><span data-stu-id="99fdb-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="99fdb-109">檔案 I/O 大幅會更方便且更快`My`，其中包含各種不同的方法和屬性的操作檔案、 目錄和磁碟機。</span><span class="sxs-lookup"><span data-stu-id="99fdb-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="99fdb-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser>物件可讓您讀取大型的結構化的檔案有分隔或固定寬度的欄位。</span><span class="sxs-lookup"><span data-stu-id="99fdb-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="99fdb-111">這個範例會開啟`TextFieldParser``reader`並使用它來讀取`C:\TestFolder1\test1.txt`。</span><span class="sxs-lookup"><span data-stu-id="99fdb-111">This example opens the `TextFieldParser``reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 <span data-ttu-id="99fdb-112">`My.Application`可讓您變更您的應用程式的文化特性。</span><span class="sxs-lookup"><span data-stu-id="99fdb-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="99fdb-113">下列範例會示範如何呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="99fdb-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="99fdb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99fdb-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [<span data-ttu-id="99fdb-115">My 如何相依於專案類型</span><span class="sxs-lookup"><span data-stu-id="99fdb-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
