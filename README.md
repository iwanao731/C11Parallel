# C++11 並列計算 忘備録

    /* paralel computing using C++11 */

    std::vector<std::thread> workers;
    std::atomic<int> i(0);

    int numThreads = std::thread::hardware_concurrency();
    numThreads = (numThreads < 1) ? 1 : numThreads;

    for (auto t = 0; t < numThreads; t++) {
    	workers.push_back(std::thread([&, t]() {
    	int index = 0;

    	while ((index = i++) < m_normalParticles.size()) { // m_normalParticles.size()-1 ??
    		/* 処理 */
    	}
    	}));
    }

    for (auto &t : workers) {
    	t.join();
    }
