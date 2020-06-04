---
title: 如何：驗證檔案名稱和路徑
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: 3b4695dfbcaf05c73bd53af5be7a49d081eb8e47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410576"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>如何：在 Visual Basic 中驗證檔案名稱和路徑
這個範例會傳回一個 `Boolean` 值，指出字串代表的是檔案名或路徑。 驗證會檢查名稱是否包含檔案系統不允許的字元。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 這個範例不會檢查名稱是否有不正確地放置冒號或沒有名稱的目錄，或者，如果名稱的長度超過系統定義的最大長度，則為。 此外，它也不會檢查應用程式是否有許可權可以存取具有指定名稱的檔案系統資源。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [在 Visual Basic 中驗證字串](validating-strings.md)
