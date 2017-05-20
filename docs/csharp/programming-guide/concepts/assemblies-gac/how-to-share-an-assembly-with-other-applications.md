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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 1e6ddb6fcee23bbabd66d9295c5ff1534140175a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>如何：與其他應用程式共用組件 (C#)
組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。  
  
 為了與其他應用程式共用組件，必須將該組件放在[全域組件快取](../../../../framework/app-domains/gac.md) (GAC) 中。  
  
### <a name="sharing-an-assembly"></a>共用組件  
  
1.  建立您的組件。 如需詳細資訊，請參閱[建立組件](../../../../framework/app-domains/create-assemblies.md)。  
  
2.  為您的組件指派強式名稱。 如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。  
  
3.  將版本資訊指派給您的組件。 如需詳細資訊，請參閱[組件版本控制](https://msdn.microsoft.com/library/51ket42z)。  
  
4.  將您的組件新增至全域組件快取。 如需詳細資訊，請參閱[如何：將組件安裝到全域組件快取](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)。  
  
5.  從其他應用程式存取組件內含的類型。 如需詳細資訊，請參閱[如何：參考以強式名稱命名的組件](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../../csharp/programming-guide/index.md)   
 [使用組件設計程式](../../../../framework/app-domains/programming-with-assemblies.md)
