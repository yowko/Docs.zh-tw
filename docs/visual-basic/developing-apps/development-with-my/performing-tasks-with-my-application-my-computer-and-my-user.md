---
title: 使用 My.Application、My.Computer 及 My.User 執行工作
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: fc9fd9093a3db4785bfc94719dbae9ec1d586050
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329584"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="90aa4-102">使用 My.Application、My.Computer 和 My.User 執行工作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90aa4-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>

<span data-ttu-id="90aa4-103">提供資訊和常用功能存取權的三個中央 `My` 物件是 `My.Application` （<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>）、`My.Computer` （<xref:Microsoft.VisualBasic.Devices.Computer>）和 `My.User` （<xref:Microsoft.VisualBasic.ApplicationServices.User>）。</span><span class="sxs-lookup"><span data-stu-id="90aa4-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="90aa4-104">您可以使用這些物件來存取與目前應用程式、應用程式安裝所在的電腦，或是應用程式目前的使用者相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="90aa4-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="90aa4-105">我的應用程式、我的電腦和我的使用者。</span><span class="sxs-lookup"><span data-stu-id="90aa4-105">My.Application, My.Computer, and My.User</span></span>  

 <span data-ttu-id="90aa4-106">下列範例示範如何使用 `My`來抓取資訊。</span><span class="sxs-lookup"><span data-stu-id="90aa4-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 <span data-ttu-id="90aa4-107">除了抓取資訊之外，透過這三個物件公開的成員也可讓您執行與該物件相關的方法。</span><span class="sxs-lookup"><span data-stu-id="90aa4-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="90aa4-108">例如，您可以存取各種不同的方法來操作檔案，或透過 `My.Computer`更新登錄。</span><span class="sxs-lookup"><span data-stu-id="90aa4-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="90aa4-109">使用 `My`，檔案 i/o 會大幅簡化且更快速，其中包括用來管理檔案、目錄和磁片磁碟機的各種方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="90aa4-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="90aa4-110"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 物件可讓您從具有分隔或固定寬度欄位的大型結構化檔案中讀取。</span><span class="sxs-lookup"><span data-stu-id="90aa4-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="90aa4-111">這個範例會開啟 `TextFieldParser` `reader`，並使用它從 `C:\TestFolder1\test1.txt`讀取。</span><span class="sxs-lookup"><span data-stu-id="90aa4-111">This example opens the `TextFieldParser` `reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 <span data-ttu-id="90aa4-112">`My.Application` 可讓您變更應用程式的文化特性。</span><span class="sxs-lookup"><span data-stu-id="90aa4-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="90aa4-113">下列範例會示範如何呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="90aa4-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="90aa4-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="90aa4-114">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="90aa4-115">My 如何相依於專案類型</span><span class="sxs-lookup"><span data-stu-id="90aa4-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
