import React, { useState, useEffect } from 'react';
import { initializeApp } from 'firebase/app';
import { 
  getAuth, 
  signInWithCustomToken, 
  signInAnonymously, 
  onAuthStateChanged, 
  GoogleAuthProvider, 
  signInWithPopup,
  signOut 
} from 'firebase/auth';
import { 
  getFirestore, 
  collection, 
  doc, 
  onSnapshot, 
  addDoc,
  deleteDoc
} from 'firebase/firestore';
import { 
  FileText, 
  Table, 
  Upload, 
  Save, 
  Trash2, 
  Loader2, 
  LogOut, 
  Search,
  ChevronRight,
  Database,
  BrainCircuit,
  FileType,
  Download,
  Settings,
  Key
} from 'lucide-react';

// --- Firebase Configuration ---
const firebaseConfig = JSON.parse(__firebase_config);
const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const db = getFirestore(app);
const appId = typeof __app_id !== 'undefined' ? __app_id : 'research-summarizer-nsbm';

const App = () => {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  const [status, setStatus] = useState({ loading: false, message: '' });
  const [savedArticles, setSavedArticles] = useState([]);
  const [view, setView] = useState('upload'); 
  const [searchTerm, setSearchTerm] = useState('');
  const [customApiKey, setCustomApiKey] = useState(localStorage.getItem('gemini_api_key') || '');
  const [showSettings, setShowSettings] = useState(false);
  
  const initialTableData = {
    relevantJournalArticle: '',
    author: '',
    year: '',
    publisher: '',
    journalRank: '',
    link: '',
    theoreticalFacts: '',
    practicalFacts: '',
    mainObjective: '',
    specificObjectives: '',
    mainResearchQuestion: '',
    specificResearchQuestions: '',
    hypothesis: '',
    population: '',
    samplingMethod: '',
    sampleSize: '',
    dataAnalysisMethod: ''
  };

  const [tableData, setTableData] = useState(initialTableData);

  // --- Load External Libraries ---
  useEffect(() => {
    const scripts = [
      { id: 'pdf-js', src: 'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js' },
      { id: 'mammoth-js', src: 'https://cdnjs.cloudflare.com/ajax/libs/mammoth/1.6.0/mammoth.browser.min.js' }
    ];
    scripts.forEach(s => {
      if (!document.getElementById(s.id)) {
        const script = document.createElement('script');
        script.id = s.id;
        script.src = s.src;
        script.async = true;
        document.head.appendChild(script);
      }
    });
    setTimeout(() => {
      if (window.pdfjsLib) window.pdfjsLib.GlobalWorkerOptions.workerSrc = 'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js';
    }, 1000);
  }, []);

  // --- Auth & Data Listeners ---
  useEffect(() => {
    const initAuth = async () => {
      if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
        await signInWithCustomToken(auth, __initial_auth_token);
      } else {
        await signInAnonymously(auth);
      }
    };
    initAuth();
    return onAuthStateChanged(auth, (user) => {
      setUser(user);
      setLoading(false);
    });
  }, []);

  useEffect(() => {
    if (!user) return;
    const q = collection(db, 'artifacts', appId, 'users', user.uid, 'articles');
    return onSnapshot(q, (snapshot) => {
      const data = snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));
      // Sort by timestamp
      setSavedArticles(data.sort((a, b) => (b.timestamp || 0) - (a.timestamp || 0)));
    });
  }, [user]);

  // --- Handlers ---
  const saveApiKey = (key) => {
    setCustomApiKey(key);
    localStorage.setItem('gemini_api_key', key);
    setShowSettings(false);
  };

  const handleSaveToTable = async () => {
    if (!user || !tableData.relevantJournalArticle) return;
    try {
      setStatus({ loading: true, message: 'Saving to your research matrix...' });
      const articlesRef = collection(db, 'artifacts', appId, 'users', user.uid, 'articles');
      await addDoc(articlesRef, { ...tableData, timestamp: Date.now() });
      setStatus({ loading: false, message: '' });
      setView('history');
    } catch (err) {
      console.error(err);
      setStatus({ loading: false, message: 'Error saving data.' });
    }
  };

  const downloadFullTable = () => {
    if (savedArticles.length === 0) return;

    // Headers matching your screenshot
    const headers = [
      "No", "Relevant Journal Article", "Author", "Year", "Publisher / Journal Name", 
      "Journal Rank/ Indexed Journal", "Link for the Base Article", 
      "Theoretical Facts (with Citations)", "Practical Facts (with Citations)", 
      "Main Objective", "Specific Objectives", "Main Research Question", 
      "Specific Research Questions", "Hypothesis", "Population", 
      "Sampling Method", "Sample Size", "Data Analysis Method"
    ];

    const rows = savedArticles.map((art, index) => [
      index + 1,
      `"${(art.relevantJournalArticle || '').replace(/"/g, '""')}"`,
      `"${(art.author || '').replace(/"/g, '""')}"`,
      art.year || '',
      `"${(art.publisher || '').replace(/"/g, '""')}"`,
      `"${(art.journalRank || '').replace(/"/g, '""')}"`,
      `"${(art.link || '').replace(/"/g, '""')}"`,
      `"${(art.theoreticalFacts || '').replace(/"/g, '""')}"`,
      `"${(art.practicalFacts || '').replace(/"/g, '""')}"`,
      `"${(art.mainObjective || '').replace(/"/g, '""')}"`,
      `"${(art.specificObjectives || '').replace(/"/g, '""')}"`,
      `"${(art.mainResearchQuestion || '').replace(/"/g, '""')}"`,
      `"${(art.specificResearchQuestions || '').replace(/"/g, '""')}"`,
      `"${(art.hypothesis || '').replace(/"/g, '""')}"`,
      `"${(art.population || '').replace(/"/g, '""')}"`,
      `"${(art.samplingMethod || '').replace(/"/g, '""')}"`,
      `"${(art.sampleSize || '').replace(/"/g, '""')}"`,
      `"${(art.dataAnalysisMethod || '').replace(/"/g, '""')}"`
    ]);

    const csvContent = [headers.join(','), ...rows.map(r => r.join(','))].join('\n');
    const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
    const url = URL.createObjectURL(blob);
    const link = document.createElement("a");
    link.setAttribute("href", url);
    link.setAttribute("download", `Literature_Review_Matrix_${new Date().toLocaleDateString()}.csv`);
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  };

  // --- AI Logic ---
  const summarizeWithGemini = async (text) => {
    const keyToUse = customApiKey || ""; 
    if (!keyToUse) {
      setShowSettings(true);
      setStatus({ loading: false, message: 'Please provide a Gemini API Key in settings.' });
      return;
    }

    setStatus({ loading: true, message: 'Gemini is extracting matrix data...' });
    
    const systemPrompt = `Extract information from the research paper into JSON. Keys: relevantJournalArticle, author, year, publisher, journalRank, link, theoreticalFacts, practicalFacts, mainObjective, specificObjectives, mainResearchQuestion, specificResearchQuestions, hypothesis, population, samplingMethod, sampleSize, dataAnalysisMethod. Return ONLY valid JSON. All values as strings.`;

    try {
      const response = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${keyToUse}`, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
          contents: [{ parts: [{ text: text.substring(0, 30000) }] }],
          systemInstruction: { parts: [{ text: systemPrompt }] },
          generationConfig: { responseMimeType: "application/json" }
        })
      });

      const result = await response.json();
      if (result.error) throw new Error(result.error.message);
      
      const data = JSON.parse(result.candidates[0].content.parts[0].text);
      setTableData(data);
      setStatus({ loading: false, message: '' });
    } catch (err) {
      console.error(err);
      setStatus({ loading: false, message: 'AI Error: ' + err.message });
    }
  };

  const handleFileUpload = async (e) => {
    const file = e.target.files[0];
    if (!file) return;
    setStatus({ loading: true, message: `Parsing ${file.name}...` });
    const reader = new FileReader();
    reader.onload = async (event) => {
      try {
        let text = "";
        if (file.name.endsWith('.pdf')) {
          const pdf = await window.pdfjsLib.getDocument({ data: event.target.result }).promise;
          for (let i = 1; i <= Math.min(pdf.numPages, 15); i++) {
            const page = await pdf.getPage(i);
            const content = await page.getTextContent();
            text += content.items.map(item => item.str).join(" ") + " ";
          }
        } else if (file.name.endsWith('.docx')) {
          const res = await window.mammoth.extractRawText({ arrayBuffer: event.target.result });
          text = res.value;
        } else {
          text = new TextDecoder().decode(event.target.result);
        }
        summarizeWithGemini(text);
      } catch (err) {
        setStatus({ loading: false, message: 'File processing failed.' });
      }
    };
    reader.readAsArrayBuffer(file);
  };

  if (loading) return <div className="h-screen flex items-center justify-center"><Loader2 className="animate-spin text-blue-600" /></div>;

  return (
    <div className="min-h-screen bg-slate-50 text-slate-900 font-sans">
      {/* Settings Modal */}
      {showSettings && (
        <div className="fixed inset-0 bg-black/50 z-50 flex items-center justify-center p-4">
          <div className="bg-white rounded-2xl p-6 max-w-sm w-full shadow-2xl">
            <h3 className="text-lg font-bold mb-4 flex items-center gap-2"><Key className="w-5 h-5 text-blue-600" /> API Settings</h3>
            <p className="text-sm text-slate-500 mb-4">Enter your Gemini API Key. If you have Gemini Pro, paste that key here to use its full capabilities.</p>
            <input 
              type="password"
              placeholder="Paste Gemini API Key here..."
              className="w-full p-3 border border-slate-200 rounded-xl mb-4 text-sm"
              value={customApiKey}
              onChange={(e) => setCustomApiKey(e.target.value)}
            />
            <div className="flex gap-2">
              <button onClick={() => saveApiKey(customApiKey)} className="flex-1 bg-blue-600 text-white py-2 rounded-lg font-bold">Save Key</button>
              <button onClick={() => setShowSettings(false)} className="px-4 py-2 text-slate-500 font-medium">Cancel</button>
            </div>
          </div>
        </div>
      )}

      <nav className="bg-white border-b border-slate-200 sticky top-0 z-10 shadow-sm">
        <div className="max-w-7xl mx-auto px-4 h-16 flex items-center justify-between">
          <div className="flex items-center gap-2 font-bold text-xl text-blue-700">
            <Database className="w-6 h-6" />
            <span>ScholarScribe AI</span>
          </div>
          <div className="flex items-center gap-2">
            <button onClick={() => setView('upload')} className={`px-4 py-2 rounded-lg text-sm font-medium ${view === 'upload' ? 'bg-blue-50 text-blue-700' : 'text-slate-600'}`}>Builder</button>
            <button onClick={() => setView('history')} className={`px-4 py-2 rounded-lg text-sm font-medium ${view === 'history' ? 'bg-blue-50 text-blue-700' : 'text-slate-600'}`}>Library</button>
            <button onClick={() => setShowSettings(true)} className="p-2 text-slate-400 hover:text-blue-600 transition-colors"><Settings className="w-5 h-5" /></button>
            <button onClick={() => signOut(auth)} className="p-2 text-slate-400 hover:text-red-500"><LogOut className="w-5 h-5" /></button>
          </div>
        </div>
      </nav>

      <main className="max-w-7xl mx-auto p-6">
        {view === 'upload' ? (
          <div className="space-y-6">
            <div className="bg-white rounded-2xl shadow-sm border border-slate-200 p-8">
              <div className="flex flex-col md:flex-row items-center justify-between gap-6">
                <div>
                  <h2 className="text-2xl font-bold">Literature Review Builder</h2>
                  <p className="text-slate-500">Upload articles to generate your matrix data automatically.</p>
                </div>
                <div className="flex gap-4">
                  <label className="flex items-center gap-2 bg-blue-600 text-white px-6 py-3 rounded-xl cursor-pointer hover:bg-blue-700 transition-all shadow-lg font-bold">
                    <Upload className="w-5 h-5" />
                    <span>Upload Journal</span>
                    <input type="file" className="hidden" accept=".pdf,.docx,.txt" onChange={handleFileUpload} />
                  </label>
                  <button 
                    onClick={handleSaveToTable}
                    disabled={!tableData.relevantJournalArticle || status.loading}
                    className="flex items-center gap-2 bg-emerald-600 text-white px-6 py-3 rounded-xl font-bold shadow-lg disabled:opacity-50"
                  >
                    <Save className="w-5 h-5" /> Add to Matrix
                  </button>
                </div>
              </div>
              {status.loading && (
                <div className="mt-6 p-4 bg-blue-50 text-blue-700 rounded-xl flex items-center gap-3 animate-pulse">
                  <BrainCircuit className="w-5 h-5" /> {status.message}
                </div>
              )}
            </div>

            <div className="bg-white rounded-2xl shadow-sm border border-slate-200 overflow-hidden">
              <div className="overflow-x-auto">
                <table className="w-full text-sm">
                  <tbody className="divide-y divide-slate-100">
                    {Object.entries(tableData).map(([key, value]) => (
                      <tr key={key} className="hover:bg-slate-50 transition-colors">
                        <td className="p-4 font-bold text-slate-500 w-64 bg-slate-50/50 capitalize border-r">{key.replace(/([A-Z])/g, ' $1')}</td>
                        <td className="p-4">
                          <textarea 
                            className="w-full bg-transparent border-none focus:ring-0 p-0 text-slate-700"
                            value={String(value)}
                            onChange={(e) => setTableData({...tableData, [key]: e.target.value})}
                            rows={String(value).length > 100 ? 4 : 1}
                          />
                        </td>
                      </tr>
                    ))}
                  </tbody>
                </table>
              </div>
            </div>
          </div>
        ) : (
          <div className="space-y-6">
            <div className="flex justify-between items-center">
              <h2 className="text-2xl font-bold">Literature Matrix ({savedArticles.length} Articles)</h2>
              <button 
                onClick={downloadFullTable}
                className="flex items-center gap-2 bg-slate-800 text-white px-6 py-3 rounded-xl font-bold shadow-lg hover:bg-black transition-all"
              >
                <Download className="w-5 h-5" /> Download Full Table (CSV)
              </button>
            </div>
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
              {savedArticles.map((art) => (
                <div key={art.id} className="bg-white p-6 rounded-2xl border border-slate-200 shadow-sm hover:shadow-md transition-all flex flex-col">
                  <div className="flex justify-between mb-4">
                    <span className="bg-blue-100 text-blue-700 px-2 py-1 rounded text-[10px] font-bold">{art.year}</span>
                    <button onClick={() => deleteDoc(doc(db, 'artifacts', appId, 'users', user.uid, 'articles', art.id))} className="text-slate-300 hover:text-red-500"><Trash2 className="w-4 h-4" /></button>
                  </div>
                  <h3 className="font-bold text-slate-800 line-clamp-2 mb-2">{art.relevantJournalArticle}</h3>
                  <p className="text-xs text-slate-500 mb-4 italic">{art.author}</p>
                  <div className="mt-auto pt-4 border-t border-slate-100">
                    <button 
                      onClick={() => { setTableData(art); setView('upload'); }}
                      className="text-blue-600 text-sm font-bold flex items-center gap-1 hover:underline"
                    >
                      View Full Details <ChevronRight className="w-4 h-4" />
                    </button>
                  </div>
                </div>
              ))}
            </div>
          </div>
        )}
      </main>
    </div>
  );
};

export default App;
