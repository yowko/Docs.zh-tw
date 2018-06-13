---
title: 如何：在 Visual Basic 中驗證檔案名稱和路徑
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: ab3df335bc5bba21d386bb69b12d840990e629fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647800"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>如何：在 Visual Basic 中驗證檔案名稱和路徑
這個範例會傳回`Boolean`值，指出字串是否表示檔案名稱或路徑。 驗證會檢查名稱是否包含檔案系統不允許的字元。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 此範例不會檢查，如果名稱不正確地將置於冒號或不含名稱的目錄，或名稱的長度超過系統定義的長度上限。 它也不會檢查應用程式是否具有指定名稱的檔案系統資源的存取權限。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [在 Visual Basic 中驗證字串](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
