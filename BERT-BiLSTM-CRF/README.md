# BERT在命名实体识别上的应用

**bert_lstm_ner.py** 
  
  - **main()**  
    - **processors-> NerProcessor( )**  
    数据预处理
    - **model_fn_builder( )**：  
    其定义了模型，训练，评测方法，并且使用钩子参数，加载了BERT模型的参数进行了自己模型的参数初始化过程
	    - **create_model( )**  
      		modeL核心部分
		    - **model.get_sequence_output( )**  
        		获取bert的embedding
		    - **BLSTM_CRF( )**  
        		命名实体识别模型
	    - **init_checkpoint**  
      		加载存在的ckpt文件，达到继续训练的效果
      - **mode=TRAIN**  
      训练模式
      - **mode=EVAL**  
      验证模式     
    - **estimator**  
    定义estimator封装器
    - **filed_based_convert_examples_to_features( )**  
    将数据转化为TF_Record 结构，作为模型数据输入
      - **convert_single_example( )**  
      将一个样本进行分析，然后将字转化为id, 标签转化为id,然后结构化到InputFeatures对象中
      - **Tokenizer**  
      tokenization.py封装好的，分词，如果是中文，就是分字
    - **file_based_input_fn_builder( )**  
    - **result_to_pair( )**
    - **return_report( )**
