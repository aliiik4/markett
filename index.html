import React, { useState, useEffect } from 'react';
import { LineChart, Line, BarChart, Bar, AreaChart, Area, XAxis, YAxis, CartesianGrid, Tooltip, Legend, ResponsiveContainer, ComposedChart, PieChart, Pie, Cell, ScatterChart, Scatter, RadarChart, PolarGrid, PolarAngleAxis, PolarRadiusAxis, Radar } from 'recharts';
import { TrendingUp, TrendingDown, Activity, BarChart3, Search, Star, Download, Zap, Brain, Target, Shield, Flame, Eye, Award, Sparkles, RefreshCw, DollarSign, Layers, Bell, Bookmark, Play, Pause, Bitcoin, TrendingUpDown, AlertCircle, Filter, Globe, Coins, PieChart as PieChartIcon, BarChart2 } from 'lucide-react';

const UltimateCryptoAnalyzer = () => {
  const [cryptoData, setCryptoData] = useState([]);
  const [selectedCoin, setSelectedCoin] = useState(null);
  const [coinDetails, setCoinDetails] = useState(null);
  const [loading, setLoading] = useState(false);
  const [activeTab, setActiveTab] = useState('dashboard');
  const [searchTerm, setSearchTerm] = useState('');
  const [categoryFilter, setCategoryFilter] = useState('all');
  const [sortBy, setSortBy] = useState('market_cap');
  const [topCoins, setTopCoins] = useState([]);
  const [analyzing, setAnalyzing] = useState(false);
  const [watchlist, setWatchlist] = useState([]);
  const [liveMode, setLiveMode] = useState(true);
  const [globalStats, setGlobalStats] = useState(null);
  const [fearGreedIndex, setFearGreedIndex] = useState(null);
  const [trendingCoins, setTrendingCoins] = useState([]);
  const [priceAlerts, setPriceAlerts] = useState([]);
  const [timeframe, setTimeframe] = useState('24h');
  const [portfolioValue, setPortfolioValue] = useState(100000);

  // Fetch Top 100 Crypto with detailed data
  const fetchCryptoData = async () => {
    try {
      setLoading(true);
      const response = await fetch(
        'https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=true&price_change_percentage=1h,24h,7d,30d,200d,1y'
      );
      const data = await response.json();
      
      const formatted = data.map(coin => ({
        id: coin.id,
        symbol: coin.symbol.toUpperCase(),
        name: coin.name,
        image: coin.image,
        price: coin.current_price,
        marketCap: coin.market_cap,
        marketCapRank: coin.market_cap_rank,
        volume: coin.total_volume,
        volumeMarketCapRatio: (coin.total_volume / coin.market_cap) * 100,
        change1h: coin.price_change_percentage_1h_in_currency || 0,
        change24h: coin.price_change_percentage_24h || 0,
        change7d: coin.price_change_percentage_7d_in_currency || 0,
        change30d: coin.price_change_percentage_30d_in_currency || 0,
        change200d: coin.price_change_percentage_200d_in_currency || 0,
        change1y: coin.price_change_percentage_1y_in_currency || 0,
        high24h: coin.high_24h,
        low24h: coin.low_24h,
        ath: coin.ath,
        athDate: coin.ath_date,
        athChangePercentage: coin.ath_change_percentage,
        atl: coin.atl,
        atlDate: coin.atl_date,
        atlChangePercentage: coin.atl_change_percentage,
        circulatingSupply: coin.circulating_supply,
        totalSupply: coin.total_supply,
        maxSupply: coin.max_supply,
        sparkline: coin.sparkline_in_7d?.price || [],
        lastUpdated: coin.last_updated
      }));
      
      setCryptoData(formatted);
      calculateGlobalStats(formatted);
      setLoading(false);
      return formatted;
    } catch (error) {
      console.error('Error fetching crypto:', error);
      setLoading(false);
      return [];
    }
  };

  // Fetch Fear & Greed Index
  const fetchFearGreed = async () => {
    try {
      const res = await fetch('https://api.alternative.me/fng/?limit=30');
      const data = await res.json();
      setFearGreedIndex({
        value: parseInt(data.data[0].value),
        classification: data.data[0].value_classification,
        history: data.data.map(d => ({
          date: new Date(parseInt(d.timestamp) * 1000).toLocaleDateString('en-US', { month: 'short', day: 'numeric' }),
          value: parseInt(d.value)
        })).reverse()
      });
    } catch (error) {
      console.error('Fear & Greed error:', error);
    }
  };

  // Fetch Trending Coins
  const fetchTrending = async () => {
    try {
      const res = await fetch('https://api.coingecko.com/api/v3/search/trending');
      const data = await res.json();
      setTrendingCoins(data.coins.slice(0, 7).map(c => ({
        id: c.item.id,
        symbol: c.item.symbol,
        name: c.item.name,
        image: c.item.small,
        rank: c.item.market_cap_rank,
        priceChange: c.item.data?.price_change_percentage_24h?.usd || 0
      })));
    } catch (error) {
      console.error('Trending error:', error);
    }
  };

  // Calculate Global Statistics
  const calculateGlobalStats = (data) => {
    if (!data.length) return;
    
    const totalMarketCap = data.reduce((sum, c) => sum + c.marketCap, 0);
    const total24hVolume = data.reduce((sum, c) => sum + c.volume, 0);
    const btcDominance = ((data.find(c => c.symbol === 'BTC')?.marketCap || 0) / totalMarketCap) * 100;
    const ethDominance = ((data.find(c => c.symbol === 'ETH')?.marketCap || 0) / totalMarketCap) * 100;
    
    const gainers = data.filter(c => c.change24h > 0).length;
    const losers = data.filter(c => c.change24h < 0).length;
    const neutral = data.length - gainers - losers;
    
    setGlobalStats({
      totalMarketCap,
      total24hVolume,
      btcDominance: btcDominance.toFixed(2),
      ethDominance: ethDominance.toFixed(2),
      gainers,
      losers,
      neutral,
      avgChange24h: (data.reduce((sum, c) => sum + c.change24h, 0) / data.length).toFixed(2)
    });
  };

  // Advanced Technical Analysis with RSI, MACD, Bollinger
  const calculateAdvancedTA = (sparkline) => {
    if (!sparkline || sparkline.length < 50) return null;

    // RSI Calculation
    const calculateRSI = (prices, period = 14) => {
      let gains = 0, losses = 0;
      for (let i = 1; i <= period; i++) {
        const change = prices[prices.length - i] - prices[prices.length - i - 1];
        if (change > 0) gains += change;
        else losses += Math.abs(change);
      }
      const avgGain = gains / period;
      const avgLoss = losses / period;
      const rs = avgGain / (avgLoss || 1);
      return 100 - (100 / (1 + rs));
    };

    // MACD
    const calculateEMA = (data, period) => {
      const k = 2 / (period + 1);
      let ema = data[0];
      for (let i = 1; i < data.length; i++) {
        ema = data[i] * k + ema * (1 - k);
      }
      return ema;
    };

    const ema12 = calculateEMA(sparkline, 12);
    const ema26 = calculateEMA(sparkline, 26);
    const macd = ema12 - ema26;
    const signal = calculateEMA([macd], 9);

    // Bollinger Bands
    const sma20 = sparkline.slice(-20).reduce((a, b) => a + b, 0) / 20;
    const variance = sparkline.slice(-20).reduce((a, b) => a + Math.pow(b - sma20, 2), 0) / 20;
    const stdDev = Math.sqrt(variance);

    // Support & Resistance
    const highs = [...sparkline].sort((a, b) => b - a);
    const lows = [...sparkline].sort((a, b) => a - b);

    return {
      rsi: calculateRSI(sparkline),
      macd: { value: macd, signal, histogram: macd - signal },
      bollinger: {
        upper: sma20 + (2 * stdDev),
        middle: sma20,
        lower: sma20 - (2 * stdDev),
        width: ((4 * stdDev) / sma20) * 100
      },
      sma20,
      sma50: sparkline.slice(-50).reduce((a, b) => a + b, 0) / Math.min(50, sparkline.length),
      ema12,
      ema26,
      currentPrice: sparkline[sparkline.length - 1],
      resistance: highs[Math.floor(highs.length * 0.1)],
      support: lows[Math.floor(lows.length * 0.1)]
    };
  };

  // AI-Powered Scoring System
  const calculateAIScore = (coin) => {
    let scores = {
      momentum: 0,      // 25 points
      volume: 0,        // 20 points
      technicals: 0,    // 25 points
      marketCap: 0,     // 15 points
      volatility: 0     // 15 points
    };

    // Momentum Analysis
    if (coin.change24h > 10) scores.momentum += 25;
    else if (coin.change24h > 5) scores.momentum += 20;
    else if (coin.change24h > 0) scores.momentum += 15;
    else if (coin.change24h > -5) scores.momentum += 10;
    else scores.momentum += 5;

    // Volume Analysis
    if (coin.volumeMarketCapRatio > 50) scores.volume += 20;
    else if (coin.volumeMarketCapRatio > 30) scores.volume += 15;
    else if (coin.volumeMarketCapRatio > 15) scores.volume += 10;
    else scores.volume += 5;

    // Technical Indicators
    const ta = calculateAdvancedTA(coin.sparkline);
    if (ta) {
      if (ta.rsi < 30) scores.technicals += 20; // Oversold
      else if (ta.rsi > 70) scores.technicals += 5; // Overbought
      else if (ta.rsi > 40 && ta.rsi < 60) scores.technicals += 15;
      else scores.technicals += 10;

      if (ta.macd.histogram > 0) scores.technicals += 5;
    } else {
      scores.technicals = 10;
    }

    // Market Cap Stability
    if (coin.marketCapRank <= 10) scores.marketCap += 15;
    else if (coin.marketCapRank <= 50) scores.marketCap += 12;
    else if (coin.marketCapRank <= 100) scores.marketCap += 8;
    else scores.marketCap += 5;

    // Volatility (7d change)
    const volatility = Math.abs(coin.change7d);
    if (volatility < 10) scores.volatility += 15; // Low volatility
    else if (volatility < 20) scores.volatility += 12;
    else if (volatility < 30) scores.volatility += 8;
    else scores.volatility += 5;

    const total = Object.values(scores).reduce((a, b) => a + b, 0);
    
    return {
      total,
      breakdown: scores,
      confidence: Math.min(95, 60 + (total / 3)),
      signal: total >= 80 ? 'خرید قوی' :
              total >= 65 ? 'خرید' :
              total >= 50 ? 'نگهداری' :
              total >= 35 ? 'فروش' : 'فروش قوی',
      riskLevel: volatility < 15 ? 'کم' : volatility < 30 ? 'متوسط' : 'بالا'
    };
  };

  // AI Scanner
  const runAIScanner = () => {
    setAnalyzing(true);
    
    setTimeout(() => {
      const analyzed = cryptoData.map(coin => ({
        ...coin,
        aiScore: calculateAIScore(coin)
      }));
      
      const sorted = analyzed.sort((a, b) => b.aiScore.total - a.aiScore.total);
      setTopCoins(sorted);
      setAnalyzing(false);
    }, 2000);
  };

  // Load Detailed Coin Data
  const loadCoinDetails = async (coin) => {
    setLoading(true);
    setSelectedCoin(coin);
    
    try {
      const response = await fetch(`https://api.coingecko.com/api/v3/coins/${coin.id}`);
      const data = await response.json();
      
      const ta = calculateAdvancedTA(coin.sparkline);
      const aiScore = calculateAIScore(coin);
      
      setCoinDetails({
        ...coin,
        description: data.description?.en || '',
        links: data.links,
        categories: data.categories || [],
        technicalAnalysis: ta,
        aiScore: aiScore,
        priceHistory: coin.sparkline.map((price, i) => ({
          time: new Date(Date.now() - (168 - i) * 3600000).toLocaleString('en-US', { month: 'short', day: 'numeric', hour: '2-digit' }),
          price: price,
          sma20: ta?.sma20,
          sma50: ta?.sma50,
          bbUpper: ta?.bollinger.upper,
          bbLower: ta?.bollinger.lower
        }))
      });
      
      setLoading(false);
    } catch (error) {
      console.error('Error loading coin details:', error);
      setLoading(false);
    }
  };

  // Watchlist Management
  const toggleWatchlist = (coin) => {
    const exists = watchlist.find(c => c.id === coin.id);
    if (exists) {
      setWatchlist(watchlist.filter(c => c.id !== coin.id));
    } else {
      setWatchlist([...watchlist, coin]);
    }
  };

  // Initial Load
  useEffect(() => {
    const loadData = async () => {
      await fetchCryptoData();
      await fetchFearGreed();
      await fetchTrending();
    };
    
    loadData();
    
    // Auto-refresh every 60 seconds if live mode
    const interval = setInterval(() => {
      if (liveMode) {
        fetchCryptoData();
        fetchFearGreed();
      }
    }, 60000);
    
    return () => clearInterval(interval);
  }, [liveMode]);

  // Filtering & Sorting
  const filteredData = cryptoData
    .filter(coin => {
      const matchesSearch = coin.symbol.toLowerCase().includes(searchTerm.toLowerCase()) || 
                           coin.name.toLowerCase().includes(searchTerm.toLowerCase());
      return matchesSearch;
    })
    .sort((a, b) => {
      switch(sortBy) {
        case 'market_cap': return b.marketCap - a.marketCap;
        case 'volume': return b.volume - a.volume;
        case 'change_24h': return b.change24h - a.change24h;
        case 'price': return b.price - a.price;
        default: return 0;
      }
    });

  const getChangeColor = (value) => {
    if (value > 0) return 'text-green-400';
    if (value < 0) return 'text-red-400';
    return 'text-slate-400';
  };

  const getScoreColor = (score) => {
    if (score >= 80) return 'text-emerald-400';
    if (score >= 65) return 'text-green-400';
    if (score >= 50) return 'text-blue-400';
    if (score >= 35) return 'text-yellow-400';
    return 'text-red-400';
  };

  const getScoreGradient = (score) => {
    if (score >= 80) return 'from-emerald-600 via-green-600 to-teal-600';
    if (score >= 65) return 'from-green-600 via-lime-600 to-emerald-600';
    if (score >= 50) return 'from-blue-600 via-cyan-600 to-sky-600';
    if (score >= 35) return 'from-yellow-600 via-amber-600 to-orange-600';
    return 'from-red-600 via-rose-600 to-pink-600';
  };

  const formatNumber = (num) => {
    if (num >= 1e12) return `$${(num / 1e12).toFixed(2)}T`;
    if (num >= 1e9) return `$${(num / 1e9).toFixed(2)}B`;
    if (num >= 1e6) return `$${(num / 1e6).toFixed(2)}M`;
    if (num >= 1e3) return `$${(num / 1e3).toFixed(2)}K`;
    return `$${num.toFixed(2)}`;
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-950 via-blue-950 to-purple-950 text-white p-4">
      <div className="max-w-[1920px] mx-auto">
        {/* Header */}
        <div className="mb-6 relative">
          <div className="absolute inset-0 bg-gradient-to-r from-orange-600 via-yellow-600 to-amber-600 blur-3xl opacity-20 animate-pulse"></div>
          <div className="relative flex items-center justify-between flex-wrap gap-4">
            <div className="flex items-center gap-4">
              <div className="relative">
                <Bitcoin className="w-16 h-16 text-orange-400 animate-pulse" />
                <Sparkles className="absolute -top-2 -right-2 w-8 h-8 text-yellow-400 animate-spin" style={{ animationDuration: '3s' }} />
              </div>
              <div>
                <h1 className="text-4xl md:text-5xl font-bold bg-gradient-to-r from-orange-400 via-yellow-400 to-amber-400 bg-clip-text text-transparent">
                  Ultimate Crypto Analyzer
                </h1>
                <p className="text-slate-400 mt-1">Top 100 Cryptocurrencies • AI-Powered Analysis • Real-time Data</p>
              </div>
            </div>
            
            <div className="flex items-center gap-3">
              <button
                onClick={() => setLiveMode(!liveMode)}
                className={`flex items-center gap-2 px-5 py-3 rounded-xl font-bold transition-all ${
                  liveMode ? 'bg-green-600 shadow-lg shadow-green-500/50 animate-pulse' : 'bg-slate-800'
                }`}
              >
                {liveMode ? <Play size={20} /> : <Pause size={20} />}
                {liveMode ? 'LIVE' : 'PAUSED'}
              </button>
              
              {watchlist.length > 0 && (
                <div className="flex items-center gap-2 bg-gradient-to-r from-yellow-600 to-orange-600 px-5 py-3 rounded-xl shadow-lg">
                  <Bookmark className="w-5 h-5" />
                  <span className="font-bold">{watchlist.length}</span>
                </div>
              )}
              
              <button className="px-5 py-3 bg-gradient-to-r from-blue-600 to-purple-600 rounded-xl font-bold shadow-lg hover:shadow-xl transition-all flex items-center gap-2">
                <Download size={20} />
                Export
              </button>
            </div>
          </div>
        </div>

        {/* Global Stats Dashboard */}
        {globalStats && (
          <div className="mb-6 grid grid-cols-2 md:grid-cols-4 lg:grid-cols-7 gap-4">
            <div className="bg-gradient-to-br from-orange-900/40 to-yellow-900/40 rounded-xl p-4 border-2 border-orange-500/50 backdrop-blur">
              <div className="flex items-center gap-2 mb-2">
                <Globe className="text-orange-400" size={20} />
                <span className="text-xs text-orange-300">Total Market Cap</span>
              </div>
              <div className="text-2xl font-bold">{formatNumber(globalStats.totalMarketCap)}</div>
            </div>
            
            <div className="bg-gradient-to-br from-blue-900/40 to-cyan-900/40 rounded-xl p-4 border-2 border-blue-500/50 backdrop-blur">
              <div className="flex items-center gap-2 mb-2">
                <BarChart3 className="text-blue-400" size={20} />
                <span className="text-xs text-blue-300">24h Volume</span>
              </div>
              <div className="text-2xl font-bold">{formatNumber(globalStats.total24hVolume)}</div>
            </div>
            
            <div className="bg-gradient-to-br from-yellow-900/40 to-amber-900/40 rounded-xl p-4 border-2 border-yellow-500/50 backdrop-blur">
              <div className="flex items-center gap-2 mb-2">
                <Bitcoin className="text-yellow-400" size={20} />
                <span className="text-xs text-yellow-300">BTC Dominance</span>
              </div>
              <div className="text-2xl font-bold">{globalStats.btcDominance}%</div>
            </div>
            
            <div className="bg-gradient-to-br from-purple-900/40 to-pink-900/40 rounded-xl p-4 border-2 border-purple-500/50 backdrop-blur">
              <div className="flex items-center gap-2 mb-2">
                <Coins className="text-purple-400" size={20} />
                <span className="text-xs text-purple-300">ETH Dominance</span>
              </div>
              <div className="text-2xl font-bold">{globalStats.ethDominance}%</div>
            </div>
            
            {fearGreedIndex && (
              <div className={`bg-gradient-to-br rounded-xl p-4 border-2 backdrop-blur ${
                fearGreedIndex.value > 60 ? 'from-green-900/40 to-emerald-900/40 border-green-500/50' :
                fearGreedIndex.value < 40 ? 'from-red-900/40 to-rose-900/40 border-red-500/50' :
                'from-yellow-900/40 to-amber-900/40 border-yellow-500/50'
              }`}>
                <div className="flex items-center gap-2 mb-2">
                  <Activity className={fearGreedIndex.value > 60 ? 'text-green-400' : fearGreedIndex.value < 40 ? 'text-red-400' : 'text-yellow-400'} size={20} />
                  <span className="text-xs">Fear & Greed</span>
                </div>
                <div className="text-2xl font-bold">{fearGreedIndex.value}</div>
                <div className="text-xs mt-1 opacity-80">{fearGreedIndex.classification}</div>
              </div>
            )}
            
            <div className="bg-gradient-to-br from-green-900/40 to-emerald-900/40 rounded-xl p-4 border-2 border-green-500/50 backdrop-blur">
              <div className="flex items-center gap-2 mb-2">
                <TrendingUp className="text-green-400" size={20} />
                <span className="text-xs text-green-300">Gainers</span>
              </div>
              <div className="text-2xl font-bold">{globalStats.gainers}</div>
            </div>
            
            <div className="bg-gradient-to-br from-red-900/40 to-rose-900/40 rounded-xl p-4 border-2 border-red-500/50 backdrop-blur">
              <div className="flex items-center gap-2 mb-2">
                <TrendingDown className="text-red-400" size={20} />
                <span className="text-xs text-red-300">Losers</span>
              </div>
              <div className="text-2xl font-bold">{globalStats.losers}</div>
            </div>
          </div>
        )}

        {/* Trending Coins Banner */}
        {trendingCoins.length > 0 && (
          <div className="mb-6 bg-gradient-to-r from-pink-900/30 to-purple-900/30 rounded-xl p-4 border border-pink-500/50 backdrop-blur">
            <div className="flex items-center gap-3 mb-3">
              <Flame className="w-6 h-6 text-orange-400 animate-pulse" />
              <span className="font-bold text-lg">🔥 Trending Now</span>
            </div>
            <div className="flex gap-3 overflow-x-auto pb-2">
              {trendingCoins.map((coin, idx) => (
                <div key={idx} className="flex-shrink-0 bg-slate-900/50 rounded-lg p-3 border border-slate-700 hover:border-pink-500 transition-all cursor-pointer min-w-[180px]">
                  <div className="flex items-center gap-2 mb-2">
                    <img src={coin.image} alt={coin.symbol} className="w-8 h-8 rounded-full" />
                    <div>
                      <div className="font-bold text-sm">{coin.symbol}</div>
                      <div className="text-xs text-slate-400">#{coin.rank}</div>
                    </div>
                  </div>
                  <div className={`text-sm font-bold ${getChangeColor(coin.priceChange)}`}>
                    {coin.priceChange >= 0 ? '+' : ''}{coin.priceChange.toFixed(2)}%
                  </div>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* Tabs */}
        <div className="flex gap-2 mb-6 overflow-x-auto pb-2">
          {[
            { id: 'dashboard', label: 'Dashboard', icon: Activity },
            { id: 'market', label: 'Market', icon: BarChart3 },
            { id: 'ai-scanner', label: 'AI Scanner', icon: Brain },
            { id: 'analysis', label: 'Deep Analysis', icon: TrendingUpDown },
            { id: 'portfolio', label: 'Portfolio', icon: PieChartIcon },
            { id: 'watchlist', label: 'Watchlist', icon: Bookmark },
            { id: 'alerts', label: 'Alerts', icon: Bell }
          ].map(tab => {
            const Icon = tab.icon;
            return (
              <button
                key={tab.id}
                onClick={() => setActiveTab(tab.id)}
                className={`flex items-center gap-2 px-5 py-3 rounded-xl font-bold transition-all whitespace-nowrap ${
                  activeTab === tab.id 
                    ? 'bg-gradient-to-r from-orange-600 via-yellow-600 to-amber-600 shadow-lg shadow-orange-500/50 scale-105' 
                    : 'bg-slate-900/50 text-slate-300 hover:bg-slate-800/50 border border-slate-700'
                }`}
              >
                <Icon size={20} />
                {tab.label}
              </button>
            );
          })}
        </div>

        {/* Dashboard Tab */}
        {activeTab === 'dashboard' && (
          <div className="space-y-6">
            {/* Fear & Greed Chart */}
            {fearGreedIndex && fearGreedIndex.history && (
              <div className="bg-slate-900/50 rounded-xl p-6 border border-slate-800 backdrop-blur">
                <h3 className="text-2xl font-bold mb-4 flex items-center gap-2">
                  <Activity className="text-purple-400" />
                  Fear & Greed Index (30 Days)
                </h3>
                <ResponsiveContainer width="100%" height={250}>
                  <AreaChart data={fearGreedIndex.history}>
                    <defs>
                      <linearGradient id="fearGreed" x1="0" y1="0" x2="0" y2="1">
                        <stop offset="5%" stopColor="#8B5CF6" stopOpacity={0.8}/>
                        <stop offset="95%" stopColor="#8B5CF6" stopOpacity={0}/>
                      </linearG
