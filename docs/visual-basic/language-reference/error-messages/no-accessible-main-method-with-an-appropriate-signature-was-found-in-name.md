---
title: "沒有可存取 &#39;Main &#39;中找不到具有適當簽章的方法 &#39;&lt;名稱&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords: BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f45dc17304c3c9d62b65760f2c1b5d461812a66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a>沒有可存取 &#39;Main &#39;中找不到具有適當簽章的方法 &#39;&lt;名稱&gt;&#39;
命令列應用程式必須具備`Sub Main`定義。 `Main`必須宣告為`Public Shared`如果已定義在類別中，或做為`Public`如果的模組中定義。  
  
 如需有關`Main`，請參閱[NIB: Visual Basic 版本的 Hello，World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)。  
  
 **錯誤 ID:** BC30737  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   定義`Public Sub Main`程序，為您的專案。 將它宣告為`Shared`如果且只有在類別內定義它。  
  
## <a name="see-also"></a>另請參閱  
 [NIB: Visual Basic 版本的 Hello，World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)  
 [Visual Basic 程式的結構](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)
