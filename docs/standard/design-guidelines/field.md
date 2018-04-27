---
title: 欄位設計
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 102c52a125c3f34dc027d01eecd24f13613e20c6
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="field-design"></a>欄位設計
封裝 （encapsulation） 的原則就是其中一個最重要的概念在物件導向設計。 此原則就是儲存在物件內的資料必須能夠存取只適用於該物件。  
  
 實用的方式來解譯原則是說出應該設計為型別，使到該類型 （名稱或型別變更） 的欄位才能進行變更而不會中斷以外的程式碼類型的成員。 此解譯立即意味著所有欄位必須都是私用。  
  
 因為這類欄位，根據定義，幾乎永遠不需要變更，我們可以排除這個嚴格限制，從的常數和靜態唯讀欄位。  
  
 **X 不**提供公用或受保護的執行個體欄位。  
  
 您應該提供屬性存取欄位，而不是公用或受保護，讓它們。  
  
 **✓ 不要**常數欄位使用的常數，永遠不會變更。  
  
 編譯器會直接將呼叫程式碼的 const 欄位的值。 因此，const 值永遠不會不會中斷相容性的變更。  
  
 **✓ 不要**使用公用靜態`readonly`預先定義的物件執行個體的欄位。  
  
 如果沒有預先定義的類型執行個體，請將其宣告為公用唯讀靜態欄位的型別本身。  
  
 **X 不**指派到可變動類型的執行個體`readonly`欄位。  
  
 可變動類型是具現化之後可修改的執行個體的類型。 例如，陣列中，大多數集合而言和資料流是可變動的型別，但<xref:System.Int32?displayProperty=nameWithType>， <xref:System.Uri?displayProperty=nameWithType>，和<xref:System.String?displayProperty=nameWithType>全都是不變。 上的參考類型欄位的唯讀修飾詞可避免被取代的欄位中儲存的執行個體，但它不會防止欄位的執行個體資料變更的執行個體的呼叫成員被修改。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
