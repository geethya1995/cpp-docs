---
title: "Compiler Error CS1654 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1654"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1654"
ms.assetid: 471c1298-1908-449d-b765-8dc3cd81a11d
caps.latest.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
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
# Compiler Error CS1654
Cannot modify members of 'variable' because it is a 'read-only variable type'  
  
 This error occurs when you try to modify members of a variable which is read-only because it is in a special construct.  
  
 One common area that this occurs is within [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) loops. It is a compile-time error to modify the value of the collection elements. Therefore, you cannot make any modifications to elements that are [value types](/dotnet/csharp/language-reference/keywords/value-types), including [structs](/dotnet/csharp/programming-guide/classes-and-structs/structs). In a collection whose elements are [reference types](/dotnet/csharp/language-reference/keywords/reference-types), you can modify accessible members of each element, but any try to add or remove or replace complete elements will generate [Compiler Error CS1656](/dotnet/csharp/language-reference/compiler-messages/cs1656).  
  
## Example  
 The following example generates error CS1654 because `Book` is a `struct`. To fix the error, change the `struct` to a [class](/dotnet/csharp/language-reference/keywords/class).  
  
```  
using System.Collections.Generic;  
using System.Text;  
  
namespace CS1654  
{  
  
    struct Book  
    {  
        public string Title;  
        public string Author;  
        public double Price;  
        public Book(string t, string a, double p)  
        {  
            Title=t;  
            Author=a;  
            Price=p;  
  
        }  
    }  
  
    class Program  
    {  
        List<Book> list;  
        static void Main(string[] args)  
        {  
             //Use a collection initializer to initialize the list  
            Program prog = new Program();  
            prog.list = new List<Book>();  
            prog.list.Add(new Book ("The C# Programming Language",  
                                    "Hejlsberg, Wiltamuth, Golde",  
                                     29.95));  
            prog.list.Add(new Book ("The C++ Programming Language",  
                                    "Stroustrup",  
                                     29.95));  
            prog.list.Add(new Book ("The C Programming Language",  
                                    "Kernighan, Ritchie",  
                                    29.95));  
            foreach(Book b in prog.list)  
            {  
                //Compile error if Book is a struct  
                //Make Book a class to modify its members  
                b.Price +=9.95; // CS1654  
            }  
  
        }  
    }  
}  
  
```