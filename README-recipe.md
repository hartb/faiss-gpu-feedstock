This conda recipe is adapted from the recipe in the upstream faiss repo:

https://github.com/facebookresearch/faiss/tree/master/conda/faiss-gpu


To build the faiss-gpu package locally, ensure your .condarc includes the
Watson Machine Learning Community Edition conda channel, with channel priority
set to strict:

    $ conda config --prepend channels https://public.dhe.ibm.com/ibmdl/export/pub/software/server/ibm-ai/conda/
    $ conda config --set channel_priority strict

Then build build the package from the recipe:

    $ conda build recipe

If the build succeeds the `fbaiss-gpu` package will be left in the 'local'
repository. You can add that channel, install fbaiss, and run with:

    $ conda config --prepend channels local
    $ conda create -n my_faiss_env faiss-gpu
    $ conda activate my_faiss_env
    (my_faiss_env) $ python -c "import faiss, numpy; print(faiss.Kmeans(10, 20).train(numpy.random.rand(1000, 10).astype('float32')))"
    478.7325744628906   # output will vary, but no complaints or errors
