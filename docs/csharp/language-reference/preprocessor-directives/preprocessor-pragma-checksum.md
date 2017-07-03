---
title: "#<a name=\"pragma-checksum-c-reference--microsoft-docs\"></a>pragma 總和檢查碼 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7acce171d3867512997d3c6fc3b42c4fc92dda18
ms.openlocfilehash: f11f6ad4206fc4c83b91da2e6e7ca0be71783134
ms.contentlocale: zh-tw
ms.lasthandoff: 07/03/2017

---
# <a name="pragma-checksum-c-reference"></a>#pragma 總和檢查碼 (C# 參考)
產生來源檔案的總和檢查碼協助偵錯[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]頁面。  
  
## <a name="syntax"></a>語法  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a>參數  
 `"filename"`  
 需要監視是否有變更或更新的檔案名稱。  
  
 `"{guid}"`  
 檔案的全域唯一識別碼 (GUID)。  
  
 `"checksum_bytes"`  
 代表總和檢查碼位元組的十六進位數字字串。 必須是偶數的十六進位數字。 奇數的數字會導致編譯時期警告，並且忽略指示詞。  
  
## <a name="remarks"></a>備註  
 Visual Studio 偵錯工具會使用總和檢查碼來確定一定會找到正確的來源。 編譯器會計算來源檔案的總和檢查碼，然後將輸出發至程式資料庫 (PDB) 檔案。 然後偵錯工具會使用 PDB 比較總和檢查碼計算來源檔案。  
  
 這個解決方案不適用於 [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] 專案，因為計算過的總和檢查碼適合產生的來源檔案，不是 .aspx 檔案。 若要解決這個問題，`#pragma checksum` 會為 [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] 頁面提供總和檢查碼支援。  
  
 當您在 [!INCLUDE[csprcs](~/includes/csprcs-md.md)] 中建立 [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] 專案時，產生的來源檔案會包含 .aspx 檔案的總和檢查碼，來源於此產生。 接著編譯器會將這項資訊寫入 PDB 檔案中。  
  
 如果編譯器在檔案中未遇到任何 `#pragma checksum` 指示詞，它會計算總和檢查碼並將值寫入 PDB 檔案。  
  
## <a name="example"></a>範例  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)

