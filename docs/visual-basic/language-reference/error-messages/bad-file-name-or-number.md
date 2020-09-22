---
title: 不正確的檔名或數目
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: d57a9e78e6ae179d3050e5a92399ca731fa16ba7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874905"
---
# <a name="bad-file-name-or-number"></a>不正確的檔名或數目

嘗試存取指定的檔案時發生錯誤。 此錯誤的可能原因包括：  
  
- 語句參考的檔案中，沒有在語句中指定的檔案名或數位， `FileOpen` 或是在語句中指定 `FileOpen` 但之後關閉的檔案。  
  
- 語句所參考的檔案，其數位超出檔案數目範圍。  
  
- 語句參考的檔案名或號碼無效。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定已在語句中指定檔案名 `FileOpen` 。 請注意，如果您叫 `FileClose` 用沒有引數的語句，您可能會不小心關閉所有開啟的檔案。  
  
2. 如果您的程式碼會產生檔案號碼演算法，請確定數位有效。  
  
3. 請檢查檔案名，以確定它們符合作業系統慣例。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Visual Basic 命名慣例](../../programming-guide/program-structure/naming-conventions.md)
