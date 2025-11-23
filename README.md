<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BIG HOUSE IN FRANCE - Pitch Deck</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- FontAwesome pour les icônes -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- React & ReactDOM -->
    <script crossorigin src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
    
    <!-- Babel pour compiler le JSX -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

    <style>
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fadeIn {
            animation: fadeIn 0.5s ease-out forwards;
        }
        body {
            background-color: #111827; /* gray-900 */
        }
    </style>
</head>
<body>
    <div id="root"></div>

    <script type="text/babel">
        const { useState, useEffect } = React;

        const Presentation = () => {
            const [currentSlide, setCurrentSlide] = useState(0);
            const totalSlides = 10;

            const nextSlide = () => setCurrentSlide((prev) => (prev + 1) % totalSlides);
            const prevSlide = () => setCurrentSlide((prev) => (prev - 1 + totalSlides) % totalSlides);

            useEffect(() => {
                const handleKeyDown = (e) => {
                    if (e.key === 'ArrowRight' || e.key === ' ') nextSlide();
                    else if (e.key === 'ArrowLeft') prevSlide();
                };
                window.addEventListener('keydown', handleKeyDown);
                return () => window.removeEventListener('keydown', handleKeyDown);
            }, []);

            const SlideContent = ({ index }) => {
                switch (index) {
                    case 0: // TITRE
                        return (
                            <div className="flex flex-col items-center justify-center h-full text-center space-y-8 animate-fadeIn">
                                <div className="w-full max-w-4xl h-64 bg-gradient-to-r from-purple-600 to-blue-600 rounded-xl shadow-2xl flex items-center justify-center mb-8 relative overflow-hidden group">
                                    <div className="absolute inset-0 bg-black opacity-30 group-hover:opacity-20 transition-opacity"></div>
                                    <h1 className="text-5xl md:text-8xl font-black text-white z-10 tracking-tighter drop-shadow-lg leading-tight">
                                        BIG HOUSE <br/> <span className="text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 to-pink-500">IN FRANCE</span>
                                    </h1>
                                </div>
                                <h2 className="text-2xl md:text-3xl font-bold text-gray-200">La plus grande maison des influenceurs & jeu de compétition</h2>
                                <div className="bg-gray-800 px-6 py-3 rounded-full border border-purple-500/50">
                                    <p className="text-xl text-purple-300 font-semibold">« 60 participants • 5 jours • 1 gagnant »</p>
                                </div>
                            </div>
                        );
                    case 1: // CONCEPT
                        return (
                            <div className="h-full flex flex-col justify-center animate-fadeIn">
                                <h2 className="text-4xl font-bold text-white mb-12 border-l-8 border-purple-500 pl-6">Concept du projet</h2>
                                <div className="grid grid-cols-1 md:grid-cols-2 gap-8">
                                    <div className="bg-gray-800 p-6 rounded-xl border border-gray-700 hover:border-purple-500 transition-all">
                                        <i className="fa-solid fa-bullseye text-4xl text-purple-400 mb-4"></i>
                                        <h3 className="text-xl font-bold text-white mb-2">Objectif</h3>
                                        <p className="text-gray-300">Créer un show immersif combinant codes de la télé-réalité, jeu d'élimination et puissance des influenceurs.</p>
                                    </div>
                                    <div className="bg-gray-800 p-6 rounded-xl border border-gray-700 hover:border-purple-500 transition-all">
                                        <i className="fa-solid fa-tv text-4xl text-blue-400 mb-4"></i>
                                        <h3 className="text-xl font-bold text-white mb-2">Format</h3>
                                        <p className="text-gray-300">5 jours de compétition + Finale en prime time + Release Party événementielle.</p>
                                    </div>
                                    <div className="bg-gray-800 p-6 rounded-xl border border-gray-700 hover:border-purple-500 transition-all">
                                        <i className="fa-solid fa-users text-4xl text-pink-400 mb-4"></i>
                                        <h3 className="text-xl font-bold text-white mb-2">Audience Cible</h3>
                                        <p className="text-gray-300">15-35 ans, consommateurs de Twitch, TikTok et fans de contenus viraux.</p>
                                    </div>
                                    <div className="bg-gray-800 p-6 rounded-xl border border-gray-700 hover:border-purple-500 transition-all">
                                        <i className="fa-solid fa-coins text-4xl text-yellow-400 mb-4"></i>
                                        <h3 className="text-xl font-bold text-white mb-2">Monétisation</h3>
                                        <p className="text-gray-300">Snapchat Shows, YouTube, Twitch (Subs/Dons), Partenariats marques intégrés.</p>
                                    </div>
                                </div>
                            </div>
                        );
                    case 2: // CHRONOLOGIE
                        return (
                            <div className="h-full flex flex-col justify-center animate-fadeIn">
                                <h2 className="text-4xl font-bold text-white mb-8 border-l-8 border-blue-500 pl-6">Chronologie du jeu</h2>
                                <div className="space-y-4 overflow-y-auto pr-2 max-h-[60vh]">
                                    {[
                                        { date: "Lun 30 mars", event: "60 participants → 10 éliminés", color: "border-red-500" },
                                        { date: "Mar 31 mars", event: "50 participants → 20 éliminés", color: "border-orange-500" },
                                        { date: "Mer 01 avril", event: "30 participants → 15 éliminés", color: "border-yellow-500" },
                                        { date: "Jeu 02 avril", event: "15 participants → 7 éliminés", color: "border-green-500" },
                                        { date: "Ven 03 avril", event: "Demi-finale : 8 participants → 4 éliminés", color: "border-blue-500" },
                                        { date: "Jeu 10 avril", event: "⭐ FINALE : 4 finalistes → 1 GAGNANT", color: "border-purple-500 bg-purple-900/20" },
                                        { date: "Post-Finale", event: "Release Party (21h30 - 02h00) : Participants, VIP, Marques", color: "border-pink-500" },
                                    ].map((item, idx) => (
                                        <div key={idx} className={`flex items-center bg-gray-800 p-4 rounded-lg border-l-4 ${item.color} ${item.bg || ''}`}>
                                            <i className="fa-regular fa-calendar text-2xl text-gray-400 mr-4 flex-shrink-0"></i>
                                            <div>
                                                <span className="block text-sm font-bold text-gray-400 uppercase tracking-wider">{item.date}</span>
                                                <span className="text-lg text-white font-medium">{item.event}</span>
                                            </div>
                                        </div>
                                    ))}
                                </div>
                            </div>
                        );
                    case 3: // RECOMPENSES
                        return (
                            <div className="h-full flex flex-col justify-center animate-fadeIn">
                                <h2 className="text-4xl font-bold text-white mb-10 border-l-8 border-yellow-500 pl-6">Récompenses & Cachets</h2>
                                <div className="flex flex-col md:flex-row gap-6 mb-8">
                                    <div className="flex-1 bg-gradient-to-br from-yellow-600 to-yellow-800 p-8 rounded-2xl shadow-lg transform hover:scale-105 transition-transform text-center border border-yellow-400">
                                        <i className="fa-solid fa-trophy text-6xl text-yellow-200 mx-auto mb-4"></i>
                                        <h3 className="text-2xl font-black text-white mb-2">LE GAGNANT</h3>
                                        <p className="text-5xl font-bold text-white">50 000 €</p>
                                        <p className="text-yellow-200 mt-2 text-sm">Cash Prize</p>
                                    </div>
                                    <div className="flex-1 bg-gray-800 p-8 rounded-2xl shadow-lg border border-gray-600 flex flex-col justify-center">
                                        <h3 className="text-xl font-bold text-blue-400 mb-4">Finalistes (Perdants)</h3>
                                        <div className="flex items-center mb-2">
                                            <div className="w-2 h-2 bg-blue-500 rounded-full mr-2"></div>
                                            <p className="text-white">Voyage 4 jours à Dubaï</p>
                                        </div>
                                    </div>
                                </div>
                                <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                                    <div className="bg-gray-800 p-5 rounded-lg border-l-4 border-green-500">
                                        <h4 className="text-lg font-bold text-gray-200">Cachets Participants</h4>
                                        <p className="text-2xl font-mono text-green-400">250 € <span className="text-sm text-gray-500">/ jour</span></p>
                                        <p className="text-xs text-gray-500 mt-1">Calculé au prorata des éliminations</p>
                                    </div>
                                    <div className="bg-gray-800 p-5 rounded-lg border-l-4 border-indigo-500">
                                        <h4 className="text-lg font-bold text-gray-200">Cachets Intervenants</h4>
                                        <p className="text-white">Standard: <span className="font-mono text-indigo-400">400 €</span> / 4h</p>
                                        <p className="text-white">Finale: <span className="font-mono text-indigo-400">3 000 €</span></p>
                                    </div>
                                </div>
                            </div>
                        );
                    case 4: // BUDGET
                        return (
                            <div className="h-full flex flex-col justify-center animate-fadeIn">
                                <h2 className="text-4xl font-bold text-white mb-8 border-l-8 border-red-500 pl-6">Budget Prévisionnel</h2>
                                <div className="flex flex-col md:flex-row gap-8">
                                    <div className="flex-1 space-y-4">
                                        {[
                                            { label: "Logistique & Production", val: "83 100 €", pct: "44%", color: "bg-blue-600" },
                                            { label: "Prix Gagnant", val: "50 000 €", pct: "26%", color: "bg-yellow-500" },
                                            { label: "Participants (Cachets)", val: "41 750 €", pct: "22%", color: "bg-purple-600" },
                                            { label: "Intervenants", val: "15 000 €", pct: "8%", color: "bg-gray-500" },
                                        ].map((item, i) => (
                                            <div key={i} className="bg-gray-800 p-4 rounded-lg">
                                                <div className="flex justify-between mb-2">
                                                    <span className="text-gray-300 font-medium">{item.label}</span>
                                                    <span className="text-white font-bold">{item.val}</span>
                                                </div>
                                                <div className="w-full bg-gray-700 h-3 rounded-full overflow-hidden">
                                                    <div className={`${item.color} h-full`} style={{ width: item.pct }}></div>
                                                </div>
                                            </div>
                                        ))}
                                    </div>
                                    <div className="md:w-1/3 bg-gray-900 p-6 rounded-xl border border-gray-700 flex flex-col justify-center items-center text-center">
                                        <p className="text-gray-400 uppercase tracking-widest text-sm mb-2">Total Dépenses</p>
                                        <p className="text-4xl font-black text-red-500">189 850 €</p>
                                    </div>
                                </div>
                            </div>
                        );
                    case 5: // REVENUS
                        return (
                            <div className="h-full flex flex-col justify-center animate-fadeIn">
                                <h2 className="text-4xl font-bold text-white mb-8 border-l-8 border-green-500 pl-6">Revenus Prévisionnels</h2>
                                <div className="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
                                    <div className="bg-gray-800 p-6 rounded-xl text-center border-t-4 border-green-400">
                                        <div className="text-green-400 font-bold text-lg mb-2">Partenariats Marques</div>
                                        <div className="text-3xl text-white font-black">250 000 €</div>
                                        <div className="text-sm text-gray-500 mt-2">Sponsors principaux & placements</div>
                                    </div>
                                    <div className="bg-gray-800 p-6 rounded-xl text-center border-t-4 border-blue-400">
                                        <div className="text-blue-400 font-bold text-lg mb-2">Monétisation Digitale</div>
                                        <div className="text-3xl text-white font-black">92 500 €</div>
                                        <div className="text-sm text-gray-500 mt-2">CPM YouTube, Subs Twitch, Snap Ads</div>
                                    </div>
                                    <div className="bg-gray-800 p-6 rounded-xl text-center border-t-4 border-pink-400">
                                        <div className="text-pink-400 font-bold text-lg mb-2">Sponsoring Party</div>
                                        <div className="text-3xl text-white font-black">30 000 €</div>
                                        <div className="text-sm text-gray-500 mt-2">Billetterie & Sponsors soirée</div>
                                    </div>
                                </div>
                                <div className="w-full bg-green-900/30 border border-green-500 p-6 rounded-xl flex justify-between items-center">
                                    <span className="text-xl text-green-100 font-bold">TOTAL REVENUS ESTIMÉS</span>
                                    <span className="text-4xl text-green-400 font-black">372 500 €</span>
                                </div>
                            </div>
                        );
                    case 6: // ANALYSE FINANCIERE
                        return (
                            <div className="h-full flex flex-col justify-center items-center animate-fadeIn text-center">
                                <h2 className="text-4xl font-bold text-white mb-12">Analyse Financière</h2>
                                <div className="flex flex-col md:flex-row items-center gap-8 w-full max-w-5xl">
                                    <div className="flex-1 bg-gray-800 p-8 rounded-2xl w-full">
                                        <p className="text-gray-400 mb-2">Revenus</p>
                                        <p className="text-3xl font-bold text-green-400">+372 500 €</p>
                                        <div className="my-4 border-b border-gray-600"></div>
                                        <p className="text-gray-400 mb-2">Dépenses</p>
                                        <p className="text-3xl font-bold text-red-400">-189 850 €</p>
                                    </div>
                                    <div className="text-5xl text-gray-600">=</div>
                                    <div className="flex-1 bg-gradient-to-br from-green-600 to-green-900 p-8 rounded-2xl w-full shadow-2xl border border-green-400 transform scale-110">
                                        <i className="fa-solid fa-chart-line text-5xl text-green-200 mx-auto mb-4"></i>
                                        <p className="text-green-100 mb-2 font-medium uppercase tracking-widest">Bénéfice Net</p>
                                        <p className="text-5xl font-black text-white mb-4">182 650 €</p>
                                        <div className="inline-block bg-white text-green-800 px-4 py-1 rounded-full font-bold">ROI : ~96%</div>
                                    </div>
                                </div>
                            </div>
                        );
                    case 7: // STRATEGIE MARKETING
                        return (
                            <div className="h-full flex flex-col justify-center animate-fadeIn">
                                <h2 className="text-4xl font-bold text-white mb-8 border-l-8 border-pink-500 pl-6">Stratégie Marketing</h2>
                                <div className="grid grid-cols-1 md:grid-cols-2 gap-8">
                                    <div className="bg-gray-800 p-6 rounded-xl relative overflow-hidden">
                                        <div className="absolute top-0 right-0 p-4 opacity-10"><i className="fa-regular fa-calendar text-9xl"></i></div>
                                        <h3 className="text-xl font-bold text-pink-400 mb-4">Avant l'événement</h3>
                                        <ul className="space-y-3 text-gray-300">
                                            <li className="flex items-center"><i className="fa-solid fa-share-nodes mr-2"></i> Teasing mystérieux sur TikTok</li>
                                            <li className="flex items-center"><i className="fa-solid fa-share-nodes mr-2"></i> Présentation participants (Instagram/Snap)</li>
                                            <li className="flex items-center"><i className="fa-solid fa-share-nodes mr-2"></i> Compte à rebours J-7</li>
                                        </ul>
                                    </div>
                                    <div className="bg-gray-800 p-6 rounded-xl relative overflow-hidden">
                                        <div className="absolute top-0 right-0 p-4 opacity-10"><i className="fa-solid fa-tv text-9xl"></i></div>
                                        <h3 className="text-xl font-bold text-purple-400 mb-4">Pendant l'événement</h3>
                                        <ul className="space-y-3 text-gray-300">
                                            <li className="flex items-center"><i className="fa-solid fa-share-nodes mr-2"></i> Live 24/7 (ou créneaux forts) Twitch</li>
                                            <li className="flex items-center"><i className="fa-solid fa-share-nodes mr-2"></i> Stories exclusives Snapchat</li>
                                            <li className="flex items-center"><i className="fa-solid fa-share-nodes mr-2"></i> Clips viraux immédiats sur Twitter/X</li>
                                        </ul>
                                    </div>
                                    <div className="bg-gray-800 p-6 rounded-xl relative overflow-hidden md:col-span-2">
                                        <h3 className="text-xl font-bold text-blue-400 mb-4">Objectif Global</h3>
                                        <p className="text-white text-lg font-medium text-center">Maximiser la viralité pour assurer un engagement record et satisfaire les KPIs des sponsors.</p>
                                    </div>
                                </div>
                            </div>
                        );
                    case 8: // POINTS FORTS
                        return (
                            <div className="h-full flex flex-col justify-center animate-fadeIn">
                                <h2 className="text-4xl font-bold text-white mb-10 border-l-8 border-white pl-6">Points Forts</h2>
                                <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                                    {[
                                        "Concept unique mêlant TV Réalité & Influence",
                                        "Audience native massive (cumul des followers)",
                                        "Monétisation multi-plateformes sécurisée",
                                        "Bénéfice net prévisionnel élevé",
                                        "Contenu 'Snackable' ultra-viral",
                                        "Engagement fort de la Gen Z"
                                    ].map((point, i) => (
                                        <div key={i} className="flex items-center bg-gray-800 p-5 rounded-lg border border-gray-700">
                                            <div className="w-8 h-8 rounded-full bg-green-500 flex items-center justify-center mr-4 flex-shrink-0">
                                                <span className="text-white font-bold">✓</span>
                                            </div>
                                            <span className="text-lg text-white font-medium">{point}</span>
                                        </div>
                                    ))}
                                </div>
                            </div>
                        );
                    case 9: // CONTACT
                        return (
                            <div className="flex flex-col items-center justify-center h-full text-center space-y-8 animate-fadeIn">
                                <h2 className="text-5xl font-black text-white mb-4">REJOIGNEZ L'AVENTURE</h2>
                                <p className="text-xl text-gray-300 max-w-2xl mx-auto">Investissez dans le futur du divertissement digital et associez votre image à l'événement de l'année.</p>
                                <div className="bg-gray-800 p-8 rounded-2xl shadow-2xl border border-purple-500 w-full max-w-md">
                                    <div className="space-y-8">
                                        <div className="flex flex-col items-center justify-center text-white hover:text-purple-400 transition-colors">
                                            <i className="fa-solid fa-envelope text-4xl mb-3"></i>
                                            <span className="text-xl font-semibold select-all">hamza@inf-agency.com</span>
                                        </div>
                                        <div className="w-full border-b border-gray-700"></div>
                                        <div className="flex flex-col items-center justify-center text-white hover:text-purple-400 transition-colors">
                                            <i className="fa-solid fa-phone text-4xl mb-3"></i>
                                            <span className="text-xl font-semibold select-all">+33 6 23 29 76 54</span>
                                        </div>
                                    </div>
                                </div>
                                <div className="text-sm text-gray-500 mt-12">© 2024 Big House Production - Document Confidentiel</div>
                            </div>
                        );
                    default:
                        return null;
                }
            };

            return (
                <div className="flex flex-col h-screen bg-gray-900 text-white font-sans overflow-hidden">
                    {/* Top Bar */}
                    <div className="h-14 bg-gray-950 flex items-center justify-between px-6 border-b border-gray-800">
                        <div className="text-purple-500 font-bold tracking-wider">BIG HOUSE PITCH</div>
                        <div className="text-gray-500 text-sm">Slide {currentSlide + 1} / {totalSlides}</div>
                    </div>

                    {/* Main Slide Area */}
                    <div className="flex-1 relative p-6 md:p-12 overflow-hidden flex items-center justify-center bg-gradient-to-br from-gray-900 via-gray-900 to-gray-800">
                        <div className="w-full max-w-6xl h-full relative">
                            <SlideContent index={currentSlide} />
                        </div>
                    </div>

                    {/* Bottom Controls */}
                    <div className="h-20 bg-gray-950 flex items-center justify-between px-6 border-t border-gray-800">
                        <button 
                            onClick={prevSlide}
                            className="flex items-center px-4 py-2 bg-gray-800 hover:bg-gray-700 rounded-lg transition-colors text-white disabled:opacity-50"
                            disabled={currentSlide === 0}
                        >
                            <i className="fa-solid fa-chevron-left mr-2"></i> Précédent
                        </button>

                        <div className="hidden md:flex space-x-2">
                            {Array.from({ length: totalSlides }).map((_, i) => (
                                <div 
                                    key={i} 
                                    onClick={() => setCurrentSlide(i)}
                                    className={`w-3 h-3 rounded-full cursor-pointer transition-all ${i === currentSlide ? 'bg-purple-500 scale-125' : 'bg-gray-700 hover:bg-gray-600'}`}
                                ></div>
                            ))}
                        </div>

                        <button 
                            onClick={nextSlide}
                            className="flex items-center px-4 py-2 bg-purple-600 hover:bg-purple-700 rounded-lg transition-colors text-white"
                        >
                            {currentSlide === totalSlides - 1 ? 'Terminer' : 'Suivant'} <i className="fa-solid fa-chevron-right ml-2"></i>
                        </button>
                    </div>
                </div>
            );
        };

        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<Presentation />);
    </script>
</body>
</html>