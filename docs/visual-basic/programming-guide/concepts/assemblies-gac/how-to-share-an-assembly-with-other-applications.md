---
title: "如何︰ 共用組件與其他應用程式 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8065a66c8f7c7b9ccb9125b060b0c03cde273482
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a>如何︰ 共用組件與其他應用程式 (Visual Basic)
組件可以是私人或共用︰ 根據預設，最簡單的程式中包含私用組件因為它們不能供其他應用程式。  
  
 為了與其他應用程式共用組件，它必須放在[全域組件快取](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)(GAC)。  
  
### <a name="sharing-an-assembly"></a>共用組件  
  
1.  建立您的組件。 如需詳細資訊，請參閱[建立組件](http://msdn.microsoft.com/library/54832ee9-dca8-4c8b-913c-c0b9d265e9a4)。  
  
2.  將強式名稱指派給您的組件。 如需詳細資訊，請參閱[How to︰ 使用強式名稱簽署組](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)。  
  
3.  將版本資訊指派給您的組件。 如需詳細資訊，請參閱[組件版本控制](https://msdn.microsoft.com/library/51ket42z)。  
  
4.  將您的組件加入至全域組件快取。 如需詳細資訊，請參閱[How to︰ 將組件安裝到全域組件快取](http://msdn.microsoft.com/library/a7e6f091-d02c-49ba-b736-7295cb0eb743)。  
  
5.  存取其他應用程式的組件中所包含的型別。 如需詳細資訊，請參閱[如何︰ 參考強式名稱組件](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813)。  
  
## <a name="see-also"></a>另請參閱  
 [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)
 [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [使用組件設計程式](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)
