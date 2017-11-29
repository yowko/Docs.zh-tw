---
title: "如何：在 Visual Basic 中驗證檔案名稱和路徑"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9c50d09dd7160992ffd95ececeff623a8aa93d2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="53239-102">如何：在 Visual Basic 中驗證檔案名稱和路徑</span><span class="sxs-lookup"><span data-stu-id="53239-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="53239-103">這個範例會傳回`Boolean`值，指出字串是否表示檔案名稱或路徑。</span><span class="sxs-lookup"><span data-stu-id="53239-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="53239-104">驗證會檢查名稱是否包含檔案系統不允許的字元。</span><span class="sxs-lookup"><span data-stu-id="53239-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53239-105">範例</span><span class="sxs-lookup"><span data-stu-id="53239-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 <span data-ttu-id="53239-106">此範例不會檢查，如果名稱不正確地將置於冒號或不含名稱的目錄，或名稱的長度超過系統定義的長度上限。</span><span class="sxs-lookup"><span data-stu-id="53239-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="53239-107">它也不會檢查應用程式是否具有指定名稱的檔案系統資源的存取權限。</span><span class="sxs-lookup"><span data-stu-id="53239-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53239-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53239-108">See Also</span></span>  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [<span data-ttu-id="53239-109">在 Visual Basic 中驗證字串</span><span class="sxs-lookup"><span data-stu-id="53239-109">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
