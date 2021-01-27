---
title: '如何測試參考相等 (身分識別) -c # 程式設計手冊'
description: 瞭解如何 (身分識別) 測試參考是否相等。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 148f37b37639061e84cefafc5f057e6e7b54563f
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899148"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>如何測試參考相等 (身分識別)  (c # 程式設計手冊) 

不必實作任何自訂邏輯，就能支援您類型中的參考相等比較。 此功能是透過靜態 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 方法提供給所有類型。  
  
 下列範例示範如何判斷兩個變數是否具有「參考相等」，這表示它們會參考記憶體中的相同物件。  
  
 範例中同時顯示為何 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 一律對實值類型傳回 `false`，以及為何不應使用 <xref:System.Object.ReferenceEquals%2A> 來判斷字串是否相等。  
  
## <a name="example"></a>範例  

 [!code-csharp[TestingReferenceEquality](snippets/how-to-test-for-reference-equality-identity/Program.cs)]  
  
 實作 <xref:System.Object?displayProperty=nameWithType> 通用基底類別中的 `Equals` 也會執行參考相等檢查，但最好不要使用此功能，原因是如果類別恰好覆寫方法，結果可能不如預期。 `==` 和 `!=` 運算子也同樣如此。 當它們對參考型別進行操作時，`==` 和 `!=` 的預設行為是執行參考相等檢查。 然而，衍生的類別可以多載運算子，以執行值相等檢查。 為了將錯誤的可能性降到最低，建議您在需要判斷兩個物件是否具有參考相等時，最好一律使用 <xref:System.Object.ReferenceEquals%2A>。  
  
 相同的組件中的常數字串一律由執行階段暫留。 也就是說，會維護每個唯一的常值字串只有一個執行個體。 不過，執行階段不保證暫留在執行階段建立的字串，也不保證暫留在不同組件中的兩個相等常數字串。  
  
## <a name="see-also"></a>另請參閱

- [相等比較](./equality-comparisons.md)
