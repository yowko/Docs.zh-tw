---
title: "如何：與其他應用程式共用組件 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 79397b18b67becf91d04358ea62cb2351be7d252
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>如何：與其他應用程式共用組件 (C#)
組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。  
  
 為了與其他應用程式共用組件，必須將該組件放在[全域組件快取](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC) 中。  
  
### <a name="sharing-an-assembly"></a>共用組件  
  
1.  建立您的組件。 如需詳細資訊，請參閱[建立組件](http://msdn.microsoft.com/library/54832ee9-dca8-4c8b-913c-c0b9d265e9a4)。  
  
2.  為您的組件指派強式名稱。 如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)。  
  
3.  將版本資訊指派給您的組件。 如需詳細資訊，請參閱[組件版本控制](https://msdn.microsoft.com/library/51ket42z)。  
  
4.  將您的組件新增至全域組件快取。 如需詳細資訊，請參閱[如何：將組件安裝到全域組件快取](http://msdn.microsoft.com/library/a7e6f091-d02c-49ba-b736-7295cb0eb743)。  
  
5.  從其他應用程式存取組件內含的類型。 如需詳細資訊，請參閱[如何：參考以強式名稱命名的組件](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../../csharp/programming-guide/index.md)   
 [使用組件設計程式](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)
