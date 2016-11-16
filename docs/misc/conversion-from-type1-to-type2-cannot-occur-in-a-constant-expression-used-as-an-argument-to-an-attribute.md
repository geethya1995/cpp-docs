---
title: "Conversion from &#39;&lt;type1&gt;&#39; to &#39;&lt;type2&gt;&#39; cannot occur in a constant expression used as an argument to an attribute | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30934"
  - "vbc30934"
helpviewer_keywords: 
  - "BC30934"
ms.assetid: 120e05f9-1d0e-4800-b05c-a8373e286b9b
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
translation.priority.ht: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
translation.priority.mt: 
  - "cs-cz"
  - "pl-pl"
  - "pt-br"
  - "tr-tr"
---
# Conversion from &#39;&lt;type1&gt;&#39; to &#39;&lt;type2&gt;&#39; cannot occur in a constant expression used as an argument to an attribute
An expression used for an attribute argument evaluates to a data type different from that of the corresponding attribute parameter, and [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] does not allow the required type conversion for attribute arguments.  
  
 An attribute provides metadata for the element it is applied to, and the compiler must be able to construct all the metadata at compile time. For this reason, every attribute must use values that are constant at compile time, and therefore every attribute argument must evaluate to a compile-time constant value.  
  
 Certain type conversions cannot produce values that are constant at compile time. For example, converting a `String` to a `Double` or a `Date` depends on the locale setting at run time. Other conversions, such as an array of a derived type to an array of `Object`, present a variety of problems that do not permit the compiler to allow them on attribute arguments.  
  
 **Error ID:** BC30934  
  
### To correct this error  
  
-   Use an expression that evaluates to the same data type as the corresponding parameter, as defined by the attribute.  
  
## See Also  
 [NOT IN BUILD: Attributes in Visual Basic](http://msdn.microsoft.com/en-us/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [NOT IN BUILD: Application of Attributes](http://msdn.microsoft.com/en-us/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)