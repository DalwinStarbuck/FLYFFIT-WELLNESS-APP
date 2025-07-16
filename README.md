# FLYFIT-WELLNESS-APP
Health and wellness app
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FlyFit - Your Personal Wellness Companion</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://kit.fontawesome.com/your-fontawesome-kit.js" crossorigin="anonymous"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#5D5CDE',
                        'primary-dark': '#4A49C7',
                    }
                }
            },
            darkMode: 'class'
        }
    </script>
    <style>
        .fade-in {
            animation: fadeIn 0.3s ease-in;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .progress-bar {
            transition: width 0.3s ease-in-out;
        }
        
        .card-hover {
            transition: all 0.2s ease-in-out;
        }
        
        .card-hover:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }
        
        .dark .card-hover:hover {
            box-shadow: 0 10px 25px rgba(255,255,255,0.1);
        }
    </style>
</head>
<body class="bg-white dark:bg-gray-900 text-gray-900 dark:text-white transition-colors duration-200">
    <!-- Navigation -->
    <nav class="bg-white dark:bg-gray-800 shadow-lg border-b border-gray-200 dark:border-gray-700">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16">
                <div class="flex items-center">
                    <div class="flex-shrink-0">
                        <h1 class="text-2xl font-bold text-primary">FitLife</h1>
                    </div>
                </div>
                <div class="flex items-center space-x-4">
                    <nav class="hidden md:flex space-x-8">
                        <button onclick="showView('dashboard')" class="nav-btn text-gray-500 dark:text-gray-300 hover:text-primary px-3 py-2 text-base font-medium transition-colors">Dashboard</button>
                        <button onclick="showView('meals')" class="nav-btn text-gray-500 dark:text-gray-300 hover:text-primary px-3 py-2 text-base font-medium transition-colors">Meals</button>
                        <button onclick="showView('exercise')" class="nav-btn text-gray-500 dark:text-gray-300 hover:text-primary px-3 py-2 text-base font-medium transition-colors">Exercise</button>
                        <button onclick="showView('progress')" class="nav-btn text-gray-500 dark:text-gray-300 hover:text-primary px-3 py-2 text-base font-medium transition-colors">Progress</button>
                        <button onclick="showView('profile')" class="nav-btn text-gray-500 dark:text-gray-300 hover:text-primary px-3 py-2 text-base font-medium transition-colors">Profile</button>
                    </nav>
                </div>
            </div>
        </div>
        
        <!-- Mobile menu -->
        <div class="md:hidden border-t border-gray-200 dark:border-gray-700">
            <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
                <button onclick="showView('dashboard')" class="nav-btn block px-3 py-2 text-base font-medium text-gray-500 dark:text-gray-300 hover:text-primary transition-colors">Dashboard</button>
                <button onclick="showView('meals')" class="nav-btn block px-3 py-2 text-base font-medium text-gray-500 dark:text-gray-300 hover:text-primary transition-colors">Meals</button>
                <button onclick="showView('exercise')" class="nav-btn block px-3 py-2 text-base font-medium text-gray-500 dark:text-gray-300 hover:text-primary transition-colors">Exercise</button>
                <button onclick="showView('progress')" class="nav-btn block px-3 py-2 text-base font-medium text-gray-500 dark:text-gray-300 hover:text-primary transition-colors">Progress</button>
                <button onclick="showView('profile')" class="nav-btn block px-3 py-2 text-base font-medium text-gray-500 dark:text-gray-300 hover:text-primary transition-colors">Profile</button>
            </div>
        </div>
    </nav>

    <!-- Main Content -->
    <main class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8">
        <!-- Welcome/Onboarding View -->
        <div id="welcome-view" class="px-4 py-6">
            <div class="max-w-2xl mx-auto text-center">
                <h2 class="text-4xl font-bold text-gray-900 dark:text-white mb-4">Welcome to FitLife</h2>
                <p class="text-xl text-gray-600 dark:text-gray-300 mb-8">Your personal wellness companion for achieving your health and fitness goals</p>
                
                <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6 mb-8">
                    <h3 class="text-2xl font-semibold mb-6">Let's Set Up Your Profile</h3>
                    
                    <form id="profile-setup" class="space-y-6">
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <div>
                                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Name</label>
                                <input type="text" id="setup-name" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Age</label>
                                <input type="number" id="setup-age" min="13" max="120" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                            </div>
                        </div>
                        
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <div>
                                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Current Weight (lbs)</label>
                                <input type="number" id="setup-weight" min="50" max="500" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Height (inches)</label>
                                <input type="number" id="setup-height" min="36" max="96" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                            </div>
                        </div>
                        
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Primary Goal</label>
                            <select id="setup-goal" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                                <option value="">Select your goal</option>
                                <option value="lose-weight">Lose Weight</option>
                                <option value="maintain-weight">Maintain Current Weight</option>
                                <option value="gain-muscle">Gain Muscle</option>
                                <option value="improve-fitness">Improve Overall Fitness</option>
                            </select>
                        </div>
                        
                        <div id="target-weight-section" class="hidden">
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Target Weight (lbs)</label>
                            <input type="number" id="setup-target-weight" min="50" max="500" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white">
                        </div>
                        
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Activity Level</label>
                            <select id="setup-activity" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                                <option value="">Select activity level</option>
                                <option value="sedentary">Sedentary (little or no exercise)</option>
                                <option value="light">Lightly Active (light exercise 1-3 days/week)</option>
                                <option value="moderate">Moderately Active (moderate exercise 3-5 days/week)</option>
                                <option value="very">Very Active (hard exercise 6-7 days/week)</option>
                                <option value="extra">Extra Active (very hard exercise, physical job)</option>
                            </select>
                        </div>
                        
                        <button type="submit" class="w-full bg-primary hover:bg-primary-dark text-white font-medium py-3 px-4 rounded-md transition-colors duration-200 text-base">
                            Get Started
                        </button>
                    </form>
                </div>
            </div>
        </div>

        <!-- Dashboard View -->
        <div id="dashboard-view" class="hidden px-4">
            <div class="mb-8">
                <h2 class="text-3xl font-bold text-gray-900 dark:text-white">Dashboard</h2>
                <p class="text-gray-600 dark:text-gray-300">Track your daily progress and stay motivated</p>
            </div>
            
            <!-- Daily Overview Cards -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
                <!-- Calories Card -->
                <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6 card-hover">
                    <div class="flex items-center justify-between">
                        <div>
                            <p class="text-sm font-medium text-gray-600 dark:text-gray-400">Calories Today</p>
                            <p class="text-2xl font-bold text-gray-900 dark:text-white" id="daily-calories">0</p>
                            <p class="text-sm text-gray-500 dark:text-gray-400">Goal: <span id="calorie-goal">2000</span></p>
                        </div>
                        <div class="w-16 h-16 bg-primary bg-opacity-10 rounded-full flex items-center justify-center">
                            <span class="text-primary text-2xl">🍽️</span>
                        </div>
                    </div>
                    <div class="mt-4">
                        <div class="bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                            <div id="calorie-progress" class="bg-primary h-2 rounded-full progress-bar" style="width: 0%"></div>
                        </div>
                    </div>
                </div>
                
                <!-- Exercise Card -->
                <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6 card-hover">
                    <div class="flex items-center justify-between">
                        <div>
                            <p class="text-sm font-medium text-gray-600 dark:text-gray-400">Exercise Minutes</p>
                            <p class="text-2xl font-bold text-gray-900 dark:text-white" id="daily-exercise">0</p>
                            <p class="text-sm text-gray-500 dark:text-gray-400">Goal: 30 min</p>
                        </div>
                        <div class="w-16 h-16 bg-green-500 bg-opacity-10 rounded-full flex items-center justify-center">
                            <span class="text-green-500 text-2xl">💪</span>
                        </div>
                    </div>
                    <div class="mt-4">
                        <div class="bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                            <div id="exercise-progress" class="bg-green-500 h-2 rounded-full progress-bar" style="width: 0%"></div>
                        </div>
                    </div>
                </div>
                
                <!-- Water Card -->
                <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6 card-hover">
                    <div class="flex items-center justify-between">
                        <div>
                            <p class="text-sm font-medium text-gray-600 dark:text-gray-400">Water Intake</p>
                            <p class="text-2xl font-bold text-gray-900 dark:text-white" id="daily-water">0</p>
                            <p class="text-sm text-gray-500 dark:text-gray-400">Goal: 8 glasses</p>
                        </div>
                        <div class="w-16 h-16 bg-blue-500 bg-opacity-10 rounded-full flex items-center justify-center">
                            <span class="text-blue-500 text-2xl">💧</span>
                        </div>
                    </div>
                    <div class="mt-4">
                        <div class="bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                            <div id="water-progress" class="bg-blue-500 h-2 rounded-full progress-bar" style="width: 0%"></div>
                        </div>
                    </div>
                </div>
                
                <!-- Weight Card -->
                <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6 card-hover">
                    <div class="flex items-center justify-between">
                        <div>
                            <p class="text-sm font-medium text-gray-600 dark:text-gray-400">Current Weight</p>
                            <p class="text-2xl font-bold text-gray-900 dark:text-white" id="current-weight">0</p>
                            <p class="text-sm text-gray-500 dark:text-gray-400">Target: <span id="target-weight">0</span> lbs</p>
                        </div>
                        <div class="w-16 h-16 bg-purple-500 bg-opacity-10 rounded-full flex items-center justify-center">
                            <span class="text-purple-500 text-2xl">⚖️</span>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Quick Actions -->
            <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6 mb-8">
                <h3 class="text-xl font-semibold text-gray-900 dark:text-white mb-4">Quick Actions</h3>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                    <button onclick="showView('meals')" class="bg-primary hover:bg-primary-dark text-white py-3 px-4 rounded-lg transition-colors duration-200 text-base">
                        Log Meal
                    </button>
                    <button onclick="showView('exercise')" class="bg-green-500 hover:bg-green-600 text-white py-3 px-4 rounded-lg transition-colors duration-200 text-base">
                        Log Exercise
                    </button>
                    <button onclick="addWater()" class="bg-blue-500 hover:bg-blue-600 text-white py-3 px-4 rounded-lg transition-colors duration-200 text-base">
                        Add Water Glass
                    </button>
                </div>
            </div>
            
            <!-- Today's Plan -->
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6">
                    <h3 class="text-xl font-semibold text-gray-900 dark:text-white mb-4">Today's Meals</h3>
                    <div id="daily-meals" class="space-y-3">
                        <p class="text-gray-500 dark:text-gray-400">No meals logged yet today</p>
                    </div>
                </div>
                
                <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6">
                    <h3 class="text-xl font-semibold text-gray-900 dark:text-white mb-4">Today's Exercises</h3>
                    <div id="daily-exercises" class="space-y-3">
                        <p class="text-gray-500 dark:text-gray-400">No exercises logged yet today</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Meals View -->
        <div id="meals-view" class="hidden px-4">
            <div class="mb-8">
                <h2 class="text-3xl font-bold text-gray-900 dark:text-white">Meal Planning</h2>
                <p class="text-gray-600 dark:text-gray-300">Track your nutrition and plan healthy meals</p>
            </div>
            
            <!-- Add Meal Form -->
            <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6 mb-8">
                <h3 class="text-xl font-semibold text-gray-900 dark:text-white mb-4">Log a Meal</h3>
                
                <form id="meal-form" class="space-y-4">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Meal Type</label>
                            <select id="meal-type" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                                <option value="">Select meal type</option>
                                <option value="breakfast">Breakfast</option>
                                <option value="lunch">Lunch</option>
                                <option value="dinner">Dinner</option>
                                <option value="snack">Snack</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Food Item</label>
                            <input type="text" id="meal-food" placeholder="e.g., Grilled chicken breast" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                        </div>
                    </div>
                    
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Calories</label>
                            <input type="number" id="meal-calories" min="0" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray
