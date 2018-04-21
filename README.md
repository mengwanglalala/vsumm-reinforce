# vsumm-reinforce
This is the official implementation of the AAAI'18 paper [Deep Reinforcement Learning for Unsupervised Video Summarization with Diversity-Representativeness Reward](https://arxiv.org/abs/1801.00054). The code is based on Theano (version `0.9.0`).

<div align="center">
  <img src="imgs/pipeline.jpg" alt="train" width="50%">
</div>

Pytorch implementation can be found [here](https://github.com/KaiyangZhou/pytorch-vsumm-reinforce).

## Preparation
To get the datasets and models, you will need `wget`.

Run the following commands in order
```bash
git clone https://github.com/KaiyangZhou/vsumm-reinforce
cd vsumm-reinforce
# download datasets.tar.gz
wget http://www.eecs.qmul.ac.uk/~kz303/vsumm-reinforce/datasets.tar.gz
tar -xvzf datasets.tar.gz
# download models.tar.gz
wget http://www.eecs.qmul.ac.uk/~kz303/vsumm-reinforce/models.tar.gz
tar -xvzf models.tar.gz
```

(Email me if you are unable to download these files)

## How to train
Training code is implemented in `vsum_train.py`. To train a RNN, run
```bash
python vsum_train.py --dataset datasets/eccv16_dataset_tvsum_google_pool5.h5 --max-epochs 60 --hidden-dim 256
```

## How to test
Test code is implemented in `vsum_test.py`. For example, to test with our models, simply run
```bash
python vsum_test.py -model models/model_tvsum_reinforceRNN.h5 -d tvsum
python vsum_test.py -model models/model_tvsum_reinforceRNN_sup.h5 -d tvsum
python vsum_test.py -model models/model_summe_reinforceRNN.h5 -d summe
python vsum_test.py -model models/model_summe_reinforceRNN_sup.h5 -d summe
```

Output results are saved to `log-test/results.h5`. To visualize score-vs-gtscore, you can use `visualize_results.py` by
```bash
python visualize_results.py -p log-test/result.h5
```

## Citation
```
@article{zhou2017reinforcevsumm, 
   title={Deep Reinforcement Learning for Unsupervised Video Summarization with Diversity-Representativeness Reward},
   author={Zhou, Kaiyang and Qiao, Yu and Xiang, Tao}, 
   journal={arXiv:1801.00054}, 
   year={2017} 
}
```
