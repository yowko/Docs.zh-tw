---
title: 浮點數
ms.date: 03/30/2017
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
ms.openlocfilehash: 8f5985576e966f1a853c9ee8d7bfef4b9bf6fc40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589369"
---
# <a name="floating-point-numbers"></a>浮點數
本主題說明開發人員在 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中使用浮點數值 (Floating-Point Number) 時經常遇到的一些問題。 這些問題是由電腦儲存浮點數值的方式而導致，而不是特定提供者 (例如 <xref:System.Data.SqlClient> 或 <xref:System.Data.OracleClient>) 所特有。  
  
 一般而言，浮點數值並不具有完全符合的二進位表示， 而是由電腦儲存該數值的近似值。 在不同的時間可能會使用不同的位元來表示該數值。 當浮點數值從一種表示法轉換為另一種時，該數值的最小顯著性數字可能會稍微變更。 轉換通常發生在當數值從一種型別轉型為另一種型別時。 不論轉換是發生在資料庫內、在表示資料庫值的型別之間或是在型別之間，都會造成最小顯著性數字的變更。 因為有這些變更，所以邏輯上應該相同的數值，可能因為最小顯著性數字變更而導致它們擁有不同的值。 數值的精確度位數可能會比預期的多或少。 如果將數值的格式設為字串，則該數值可能不會顯示預期的值。  
  
 若要盡可能減少這些效果，您應該就可用的項目中，選用最接近的數值型別相符項目。 例如，如果您正在使用 SQL Server，確切的數值可能會變更，如果您將實際型別的 TRANSACT-SQL 值轉換成 float 類型的值。 在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中將 <xref:System.Single> 轉換成 <xref:System.Double> 可能也會造成未預期的結果。 在上述兩種情況中，將應用程式中的所有值設定為使用相同的數字型別 (Numeric Type) 是不錯的策略。 您也可以使用固定有效位數十進位型別，或者將浮點數值轉型為固定有效位數十進位型別，再加以使用。  
  
 若要解決等號比較的問題，請考慮撰寫應用程式的程式碼，使最小顯著性數字中的變更可以忽略。 例如，與其比較兩個數字是否相等，請從一個數字中減去另一個數字。 如果差異是在可接受的捨入範圍內，則應用程式可以將這兩個數字視為相同。  
  
## <a name="see-also"></a>另請參閱
- [浮點數會失去精確度的原因](https://msdn.microsoft.com/library/1acb1add-ac06-4134-a2fd-aff13d8c4c15)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
