---
LINK:
  - " "
  - "[[Natural Language Processing NLP]]"
  - "[[Text Mining]]"
---
#java 

是一種基於機器學習的工具包，用於處理自然語言文本


<iframe width=80% height=500px src="https://opennlp.apache.org/docs/1.5.3/manual/opennlp.html#tools.sentdetect.detection"> OpenNLP 開發文檔
</iframe>
https://opennlp.apache.org/docs/1.5.3/manual/opennlp.html#tools.sentdetect.detection


 - tokenization 
 - sentence segmentation
 - part-of-speech tagging
 - named entity extraction
 - chunking, parsing 
 - coreference resolution

## API 

```Java
InputStream modelIn = **new** FileInputStream("lang-model-name.bin");

try {
  SomeModel model = **new** SomeModel(modelIn);
}
catch (IOException e) {
  //handle the exception
}
finally {
  if (null != modelIn) {
    try {
      modelIn.close();
    }
      catch(IOException e) {
    }
  }
}
```

實例化工具本身
`ToolName toolName = **new** ToolName(model);`


## Sentence Detection

```java
import java.io.FileInputStream;
import java.io.IOException;
import opennlp.tools.sentdetect.SentenceDetectorME;
import opennlp.tools.sentdetect.SentenceModel;

public class SentenceDetectionExample {
    public static void main(String[] args) throws IOException {
        // 加載模型
        FileInputStream modelIn = new FileInputStream("en-sent.bin");
        SentenceModel model = new SentenceModel(modelIn);

        // 創建句子檢測器
        SentenceDetectorME sentenceDetector = new SentenceDetectorME(model);

        // 測試文本
        String paragraph = "Hello world. OpenNLP is an NLP library.";
        String[] sentences = sentenceDetector.sentDetect(paragraph);

        // 輸出結果
        for (String sentence : sentences) {
            System.out.println(sentence);
        }

        modelIn.close();
    }
}

```


## 分詞（Tokenization）


```Java
import java.io.FileInputStream;
import java.io.IOException;
import opennlp.tools.tokenize.TokenizerME;
import opennlp.tools.tokenize.TokenizerModel;

public class TokenizationExample {
    public static void main(String[] args) throws IOException {
        // 加載模型
        FileInputStream modelIn = new FileInputStream("en-token.bin");
        TokenizerModel model = new TokenizerModel(modelIn);

        // 創建分詞器
        TokenizerME tokenizer = new TokenizerME(model);

        // 測試文本
        String text = "Hello, this is OpenNLP!";
        String[] tokens = tokenizer.tokenize(text);

        // 輸出結果
        for (String token : tokens) {
            System.out.println(token);
        }

        modelIn.close();
    }
}

```



## 詞性標註（POS Tagging）



```java
import java.io.FileInputStream;
import java.io.IOException;
import opennlp.tools.postag.POSModel;
import opennlp.tools.postag.POSTaggerME;

public class POSTaggingExample {
    public static void main(String[] args) throws IOException {
        // 加載模型
        FileInputStream modelIn = new FileInputStream("en-pos-maxent.bin");
        POSModel model = new POSModel(modelIn);

        // 創建詞性標註器
        POSTaggerME tagger = new POSTaggerME(model);

        // 測試文本
        String[] sentence = {"Hello", ",", "this", "is", "OpenNLP", "!"};
        String[] tags = tagger.tag(sentence);

        // 輸出結果
        for (int i = 0; i %3C sentence.length; i++) {
            System.out.println(sentence[i] + " -%3E " + tags[i]);
        }

        modelIn.close();
    }
}
```


常見的詞性標註（POS tags）：
- `NN`（名詞）
- `VB`（動詞）
- `JJ`（形容詞）
- `RB`（副詞




## 命名實體識別（NER）

```java
import java.io.FileInputStream;
import java.io.IOException;
import opennlp.tools.namefind.NameFinderME;
import opennlp.tools.namefind.TokenNameFinderModel;
import opennlp.tools.util.Span;

public class NERExample {
    public static void main(String[] args) throws IOException {
        // 加載模型
        FileInputStream modelIn = new FileInputStream("en-ner-person.bin");
        TokenNameFinderModel model = new TokenNameFinderModel(modelIn);

        // 創建命名實體識別器
        NameFinderME nameFinder = new NameFinderME(model);

        // 測試文本
        String[] sentence = {"John", "lives", "in", "New", "York", "."};
        Span[] names = nameFinder.find(sentence);

        // 輸出結果
        for (Span name : names) {
            System.out.println("Entity: " + name.toString());
        }

        modelIn.close();
    }
}

```
































