---
title: 使用 My.Application、My.Computer 和 My.User 執行工作 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 5340c137842591bb1f4408392e02329fb2a491ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651626"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="4c664-102">使用 My.Application、My.Computer 和 My.User 執行工作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c664-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="4c664-103">三種中央`My`提供使用功能的存取權對資訊和常用的物件`My.Application`(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>)， `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)，以及`My.User`(<xref:Microsoft.VisualBasic.ApplicationServices.User>)。</span><span class="sxs-lookup"><span data-stu-id="4c664-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="4c664-104">您可以使用這些物件分別存取與目前的應用程式、，安裝應用程式的電腦或目前使用者的應用程式時，相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c664-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="4c664-105">My.Application、 My.Computer 和 My.User</span><span class="sxs-lookup"><span data-stu-id="4c664-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="4c664-106">下列範例示範如何資訊可能會使用擷取`My`。</span><span class="sxs-lookup"><span data-stu-id="4c664-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 <span data-ttu-id="4c664-107">除了擷取資訊，透過這三個物件所公開的成員也可讓您執行該物件相關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="4c664-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="4c664-108">比方說，您可以存取各種不同的方法來操作檔案，或更新透過登錄`My.Computer`。</span><span class="sxs-lookup"><span data-stu-id="4c664-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="4c664-109">檔案 I/O 大幅會更方便且更快速地`My`，其中包含各種不同的方法和屬性來操作檔案、 目錄和磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4c664-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="4c664-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser>物件可讓您讀取已分隔的大型結構化的檔案或固定寬度的欄位。</span><span class="sxs-lookup"><span data-stu-id="4c664-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="4c664-111">此範例會開啟`TextFieldParser``reader`並使用它來讀取`C:\TestFolder1\test1.txt`。</span><span class="sxs-lookup"><span data-stu-id="4c664-111">This example opens the `TextFieldParser` `reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 <span data-ttu-id="4c664-112">`My.Application` 可讓您變更您的應用程式的文化特性。</span><span class="sxs-lookup"><span data-stu-id="4c664-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="4c664-113">下列範例會示範如何呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="4c664-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4c664-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c664-114">See also</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="4c664-115">My 如何相依於專案類型</span><span class="sxs-lookup"><span data-stu-id="4c664-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
