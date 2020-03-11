# 텐서보드로 vector embedding visualization 하기

High dimensional vector space 는 아무래도 머릿속에 잘 그려지지 않아서 TSNE 니 이런걸로 visualization 하기는 하는데, 좀 더 인터랙티브하게 보고 싶어서 텐서보드로 보는 법을 강구해봤다.

```python
import tensorflow as tf
from tensorflow.contrib.tensorboard.plugins import projector

LOGDIR = '여기에 로그 폴더를 써주세요'

embedding_var = tf.Variable(np.array(reply_vectors2), name='sentence_embedding')
config = projector.ProjectorConfig()

embedding = config.embeddings.add()
embedding.tensor_name = embedding_var.name

embedding.metadata_path = LOGDIR + 'metadata.tsv'

init_op = tf.global_variables_initializer()

with tf.Session() as sess:
    summary_writer = tf.summary.FileWriter(LOGDIR, sess.graph)
    projector.visualize_embeddings(summary_writer, config)
    sess.run(init_op)
    saver = tf.train.Saver()
    saver.save(sess, LOGDIR + 'model.ckpt', 0)
```

```python
with open(LOGDIR + 'metadata.tsv', 'w') as file:
    for sent in sentences:
        file.write('%s\n' % sent)
```

이런 식으로 해 주면 tensorboard 로 볼 수 있음. embedding tab 에서 보면 된다.



### 참조

https://www.tensorflow.org/versions/r1.0/get_started/embedding_viz
