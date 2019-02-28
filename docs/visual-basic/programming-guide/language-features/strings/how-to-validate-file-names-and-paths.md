---
title: HOW TO：驗證檔案名稱和 Visual Basic 中的路徑
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: d29553071d68319d754406b3104da6e096f908fd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975520"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>HOW TO：驗證檔案名稱和 Visual Basic 中的路徑
這個範例會傳回`Boolean`值，指出字串是否表示的檔案名稱或路徑。 驗證會檢查名稱是否包含檔案系統不允許的字元。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 此範例不會檢查，如果名稱不正確地將置於冒號或沒有同名的目錄，或名稱的長度超過系統定義的長度上限。 它也不會檢查應用程式是否有權存取指定名稱的檔案系統資源。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [在 Visual Basic 中驗證字串](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
