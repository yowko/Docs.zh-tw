---
title: 不正確的資料錄數目
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 8cbffc7714211fb10bedc3a73729eac59d98f0bb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086981"
---
# <a name="bad-record-number"></a>不正確的資料錄數目

`a FileGet`、 `FilePut`、 `FileGetObject`或 `FilePutObject` 陳述式中的資料錄數目小於或等於零。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 檢查用於產生資料錄數目的計算。 確認包含資料錄數目或用於計算資料錄數目的變數拼字正確。 除非在模組中使用 `Option Explicit On` ，否則拼錯的變數名稱會隱含宣告並初始化為零。  
  
## <a name="see-also"></a>另請參閱

- [Option Explicit 陳述式](../language-reference/statements/option-explicit-statement.md)
