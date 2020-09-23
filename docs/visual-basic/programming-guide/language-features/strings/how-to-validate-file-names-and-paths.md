---
title: 如何：驗證檔案名稱和路徑
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: b722222ea8b8088a6b326eef27147c08f8419272
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072648"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="0f830-102">如何：在 Visual Basic 中驗證檔案名稱和路徑</span><span class="sxs-lookup"><span data-stu-id="0f830-102">How to: Validate File Names and Paths in Visual Basic</span></span>

<span data-ttu-id="0f830-103">這個範例會傳回一個 `Boolean` 值，這個值會指出字串是否代表檔案名或路徑。</span><span class="sxs-lookup"><span data-stu-id="0f830-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="0f830-104">驗證會檢查名稱是否包含檔案系統不允許的字元。</span><span class="sxs-lookup"><span data-stu-id="0f830-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f830-105">範例</span><span class="sxs-lookup"><span data-stu-id="0f830-105">Example</span></span>  

 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="0f830-106">此範例不會檢查名稱是否不正確地放置冒號或沒有名稱的目錄，或者如果名稱的長度超過系統定義的最大長度。</span><span class="sxs-lookup"><span data-stu-id="0f830-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="0f830-107">此外，它也不會檢查應用程式是否有權存取具有指定名稱的檔案系統資源。</span><span class="sxs-lookup"><span data-stu-id="0f830-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f830-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f830-108">See also</span></span>

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="0f830-109">在 Visual Basic 中驗證字串</span><span class="sxs-lookup"><span data-stu-id="0f830-109">Validating Strings in Visual Basic</span></span>](validating-strings.md)
