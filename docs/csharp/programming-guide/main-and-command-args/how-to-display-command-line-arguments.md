---
title: '如何顯示命令列引數-c # 程式設計指南'
description: 瞭解如何顯示命令列引數。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 717e27c23724e63c03a38b028ef99dc6530b4745
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195476"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>如何顯示命令列引數 (c # 程式設計指南) 

在命令列上提供給可執行檔的引數可透過的選擇性參數來存取 `Main` 。 引數是以字串陣列的形式提供。 陣列的每個項目都包含一個引數。 引數之間的空白字元會被移除。 例如，請考慮這些虛擬可執行檔的命令列引動過程：  
  
|命令列上的輸入|傳遞至 Main 的字串陣列|  
|----------------------------|-------------------------------------|  
|**executable.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe one two**|"one"<br /><br /> "two"|  
|**executable.exe "one two" three**|"one two"<br /><br /> "three"|  
  
> [!NOTE]
> 在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁](/visualstudio/ide/reference/debug-page-project-designer)中指定命令列引數。  
  
## <a name="example"></a>範例  

 此範例會顯示傳遞至命令列應用程式的命令列引數。 所顯示的輸出是上表中的第一個項目。  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [使用 csc.exe 建置命令列](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [主要 ( # A1 和命令列引數](./index.md)
- [Main() 傳回值](./main-return-values.md)
