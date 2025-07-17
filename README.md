<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FitLife - Your Personal Wellness Companion</title>
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
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Protein (g)</label>
                            <input type="number" id="meal-protein" min="0" step="0.1" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white">
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Carbs (g)</label>
                            <input type="number" id="meal-carbs" min="0" step="0.1" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white">
                        </div>
                    </div>
                    
                    <button type="submit" class="bg-primary hover:bg-primary-dark text-white font-medium py-2 px-4 rounded-md transition-colors duration-200 text-base">
                        Log Meal
                    </button>
                </form>
            </div>
            
            <!-- Meal History -->
            <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6">
                <h3 class="text-xl font-semibold text-gray-900 dark:text-white mb-4">Recent Meals</h3>
                <div id="meal-history" class="space-y-4">
                    <p class="text-gray-500 dark:text-gray-400">No meals logged yet</p>
                </div>
            </div>
        </div>

        <!-- Exercise View -->
        <div id="exercise-view" class="hidden px-4">
            <div class="mb-8">
                <h2 class="text-3xl font-bold text-gray-900 dark:text-white">Exercise Tracking</h2>
                <p class="text-gray-600 dark:text-gray-300">Log your workouts and stay active</p>
            </div>
            
            <!-- Add Exercise Form -->
            <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6 mb-8">
                <h3 class="text-xl font-semibold text-gray-900 dark:text-white mb-4">Log Exercise</h3>
                
                <form id="exercise-form" class="space-y-4">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Exercise Type</label>
                            <select id="exercise-type" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                                <option value="">Select exercise type</option>
                                <option value="cardio">Cardio</option>
                                <option value="strength">Strength Training</option>
                                <option value="flexibility">Flexibility/Yoga</option>
                                <option value="sports">Sports</option>
                                <option value="other">Other</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Exercise Name</label>
                            <input type="text" id="exercise-name" placeholder="e.g., Morning jog, Push-ups" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                        </div>
                    </div>
                    
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Duration (minutes)</label>
                            <input type="number" id="exercise-duration" min="1" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Intensity</label>
                            <select id="exercise-intensity" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white" required>
                                <option value="">Select intensity</option>
                                <option value="low">Low</option>
                                <option value="moderate">Moderate</option>
                                <option value="high">High</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Calories Burned</label>
                            <input type="number" id="exercise-calories" min="0" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white">
                        </div>
                    </div>
                    
                    <button type="submit" class="bg-green-500 hover:bg-green-600 text-white font-medium py-2 px-4 rounded-md transition-colors duration-200 text-base">
                        Log Exercise
                    </button>
                </form>
            </div>
            
            <!-- Exercise History -->
            <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6">
                <h3 class="text-xl font-semibold text-gray-900 dark:text-white mb-4">Recent Exercises</h3>
                <div id="exercise-history" class="space-y-4">
                    <p class="text-gray-500 dark:text-gray-400">No exercises logged yet</p>
                </div>
            </div>
        </div>

        <!-- Progress View -->
        <div id="progress-view" class="hidden px-4">
            <div class="mb-8">
                <h2 class="text-3xl font-bold text-gray-900 dark:text-white">Progress Tracking</h2>
                <p class="text-gray-600 dark:text-gray-300">Monitor your journey and celebrate achievements</p>
            </div>
            
            <!-- Weight Tracking -->
            <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6 mb-8">
                <h3 class="text-xl font-semibold text-gray-900 dark:text-white mb-4">Weight Tracking</h3>
                
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div>
                        <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Current Weight (lbs)</label>
                        <div class="flex space-x-2">
                            <input type="number" id="weight-input" min="50" max="500" step="0.1" class="flex-1 px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white">
                            <button onclick="updateWeight()" class="bg-primary hover:bg-primary-dark text-white px-4 py-2 rounded-md transition-colors duration-200 text-base">
                                Update
                            </button>
                        </div>
                    </div>
                    
                    <div class="bg-gray-50 dark:bg-gray-700 p-4 rounded-lg">
                        <h4 class="font-medium text-gray-900 dark:text-white mb-2">Progress Summary</h4>
                        <div class="space-y-2 text-sm">
                            <div class="flex justify-between">
                                <span class="text-gray-600 dark:text-gray-400">Starting Weight:</span>
                                <span class="font-medium" id="starting-weight">0 lbs</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600 dark:text-gray-400">Current Weight:</span>
                                <span class="font-medium" id="progress-current-weight">0 lbs</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600 dark:text-gray-400">Weight Change:</span>
                                <span class="font-medium" id="weight-change">0 lbs</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600 dark:text-gray-400">Goal Progress:</span>
                                <span class="font-medium" id="goal-progress">0%</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Weekly Stats -->
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6">
                    <h3 class="text-xl font-semibold text-gray-900 dark:text-white mb-4">This Week's Overview</h3>
                    <div class="space-y-4">
                        <div class="flex justify-between items-center">
                            <span class="text-gray-600 dark:text-gray-400">Average Daily Calories</span>
                            <span class="font-medium" id="avg-calories">0</span>
                        </div>
                        <div class="flex justify-between items-center">
                            <span class="text-gray-600 dark:text-gray-400">Total Exercise Minutes</span>
                            <span class="font-medium" id="total-exercise">0</span>
                        </div>
                        <div class="flex justify-between items-center">
                            <span class="text-gray-600 dark:text-gray-400">Days Active</span>
                            <span class="font-medium" id="active-days">0/7</span>
                        </div>
                    </div>
                </div>
                
                <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6">
                    <h3 class="text-xl font-semibold text-gray-900 dark:text-white mb-4">Achievements</h3>
                    <div id="achievements" class="space-y-3">
                        <div class="flex items-center space-x-3 p-3 bg-yellow-50 dark:bg-yellow-900 rounded-lg">
                            <span class="text-2xl">🎯</span>
                            <div>
                                <p class="font-medium text-yellow-800 dark:text-yellow-200">Welcome to FitLife!</p>
                                <p class="text-sm text-yellow-600 dark:text-yellow-300">You've started your wellness journey</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Profile View -->
        <div id="profile-view" class="hidden px-4">
            <div class="mb-8">
                <h2 class="text-3xl font-bold text-gray-900 dark:text-white">Profile Settings</h2>
                <p class="text-gray-600 dark:text-gray-300">Manage your personal information and goals</p>
            </div>
            
            <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6">
                <form id="profile-form" class="space-y-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Name</label>
                            <input type="text" id="profile-name" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white">
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Age</label>
                            <input type="number" id="profile-age" min="13" max="120" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white">
                        </div>
                    </div>
                    
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Height (inches)</label>
                            <input type="number" id="profile-height" min="36" max="96" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white">
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Activity Level</label>
                            <select id="profile-activity" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white">
                                <option value="sedentary">Sedentary</option>
                                <option value="light">Lightly Active</option>
                                <option value="moderate">Moderately Active</option>
                                <option value="very">Very Active</option>
                                <option value="extra">Extra Active</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Primary Goal</label>
                            <select id="profile-goal" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white">
                                <option value="lose-weight">Lose Weight</option>
                                <option value="maintain-weight">Maintain Current Weight</option>
                                <option value="gain-muscle">Gain Muscle</option>
                                <option value="improve-fitness">Improve Overall Fitness</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Target Weight (lbs)</label>
                            <input type="number" id="profile-target-weight" min="50" max="500" class="w-full px-3 py-2 text-base border border-gray-300 dark:border-gray-600 rounded-md shadow-sm focus:outline-none focus:ring-primary focus:border-primary dark:bg-gray-700 dark:text-white">
                        </div>
                    </div>
                    
                    <button type="submit" class="bg-primary hover:bg-primary-dark text-white font-medium py-2 px-4 rounded-md transition-colors duration-200 text-base">
                        Update Profile
                    </button>
                </form>
            </div>
        </div>
    </main>

    <script>
        // Dark mode detection
        if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
            document.documentElement.classList.add('dark');
        }
        window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', event => {
            if (event.matches) {
                document.documentElement.classList.add('dark');
            } else {
                document.documentElement.classList.remove('dark');
            }
        });

        // App State
        let appState = {
            user: null,
            dailyData: {
                calories: 0,
                exercise: 0,
                water: 0,
                meals: [],
                exercises: []
            },
            history: {
                meals: [],
                exercises: [],
                weights: []
            }
        };

        // View Management
        function showView(viewName) {
            // Hide all views
            const views = ['welcome-view', 'dashboard-view', 'meals-view', 'exercise-view', 'progress-view', 'profile-view'];
            views.forEach(view => {
                document.getElementById(view).classList.add('hidden');
            });
            
            // Show selected view
            document.getElementById(viewName + '-view').classList.remove('hidden');
            document.getElementById(viewName + '-view').classList.add('fade-in');
            
            // Update navigation
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('text-primary');
                btn.classList.add('text-gray-500', 'dark:text-gray-300');
            });
            
            const activeButtons = document.querySelectorAll(`[onclick="showView('${viewName}')"]`);
            activeButtons.forEach(btn => {
                btn.classList.remove('text-gray-500', 'dark:text-gray-300');
                btn.classList.add('text-primary');
            });
            
            if (viewName === 'dashboard') {
                updateDashboard();
            } else if (viewName === 'progress') {
                updateProgress();
            }
        }

        // Custom alert function
        function showAlert(message, type = 'info') {
            const alertDiv = document.createElement('div');
            alertDiv.className = `fixed top-4 right-4 z-50 p-4 rounded-lg shadow-lg max-w-sm ${type === 'error' ? 'bg-red-500' : type === 'success' ? 'bg-green-500' : 'bg-primary'} text-white`;
            alertDiv.innerHTML = `
                <div class="flex items-center justify-between">
                    <p class="text-sm font-medium">${message}</p>
                    <button onclick="this.parentElement.parentElement.remove()" class="ml-4 text-white hover:text-gray-200">
                        <span class="text-lg">&times;</span>
                    </button>
                </div>
            `;
            document.body.appendChild(alertDiv);
            
            // Auto remove after 3 seconds
            setTimeout(() => {
                if (alertDiv.parentElement) {
                    alertDiv.remove();
                }
            }, 3000);
        }

        // Profile Setup
        document.getElementById('profile-setup').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const formData = new FormData(this);
            const userData = {
                name: document.getElementById('setup-name').value,
                age: parseInt(document.getElementById('setup-age').value),
                weight: parseFloat(document.getElementById('setup-weight').value),
                height: parseInt(document.getElementById('setup-height').value),
                goal: document.getElementById('setup-goal').value,
                targetWeight: parseFloat(document.getElementById('setup-target-weight').value) || null,
                activity: document.getElementById('setup-activity').value
            };
            
            // Calculate daily calorie goal based on user data
            const bmr = calculateBMR(userData.weight, userData.height, userData.age);
            const calorieGoal = calculateDailyCalories(bmr, userData.activity, userData.goal);
            
            appState.user = {
                ...userData,
                calorieGoal,
                startingWeight: userData.weight
            };
            
            // Initialize weight history
            appState.history.weights.push({
                date: new Date().toDateString(),
                weight: userData.weight
            });
            
            showAlert('Profile created successfully!', 'success');
            showView('dashboard');
            updateDashboard();
        });

        // Goal change handler
        document.getElementById('setup-goal').addEventListener('change', function() {
            const targetWeightSection = document.getElementById('target-weight-section');
            if (this.value === 'lose-weight' || this.value === 'gain-muscle') {
                targetWeightSection.classList.remove('hidden');
                document.getElementById('setup-target-weight').required = true;
            } else {
                targetWeightSection.classList.add('hidden');
                document.getElementById('setup-target-weight').required = false;
            }
        });

        // BMR Calculation (Mifflin-St Jeor Equation)
        function calculateBMR(weight, height, age) {
            // Assuming average of male/female for simplicity
            return (10 * (weight * 0.453592)) + (6.25 * (height * 2.54)) - (5 * age) + 5;
        }

        // Daily Calorie Calculation
        function calculateDailyCalories(bmr, activity, goal) {
            const activityMultipliers = {
                'sedentary': 1.2,
                'light': 1.375,
                'moderate': 1.55,
                'very': 1.725,
                'extra': 1.9
            };
            
            let tdee = bmr * activityMultipliers[activity];
            
            // Adjust based on goal
            if (goal === 'lose-weight') {
                tdee -= 500; // 1 lb per week deficit
            } else if (goal === 'gain-muscle') {
                tdee += 300; // Moderate surplus
            }
            
            return Math.round(tdee);
        }

        // Meal Logging
        document.getElementById('meal-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const meal = {
                id: Date.now(),
                type: document.getElementById('meal-type').value,
                food: document.getElementById('meal-food').value,
                calories: parseInt(document.getElementById('meal-calories').value),
                protein: parseFloat(document.getElementById('meal-protein').value) || 0,
                carbs: parseFloat(document.getElementById('meal-carbs').value) || 0,
                date: new Date().toDateString(),
                time: new Date().toLocaleTimeString()
            };
            
            appState.dailyData.meals.push(meal);
            appState.history.meals.push(meal);
            appState.dailyData.calories += meal.calories;
            
            this.reset();
            showAlert('Meal logged successfully!', 'success');
            updateMealHistory();
            updateDashboard();
        });

        // Exercise Logging
        document.getElementById('exercise-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const exercise = {
                id: Date.now(),
                type: document.getElementById('exercise-type').value,
                name: document.getElementById('exercise-name').value,
                duration: parseInt(document.getElementById('exercise-duration').value),
                intensity: document.getElementById('exercise-intensity').value,
                calories: parseInt(document.getElementById('exercise-calories').value) || 0,
                date: new Date().toDateString(),
                time: new Date().toLocaleTimeString()
            };
            
            appState.dailyData.exercises.push(exercise);
            appState.history.exercises.push(exercise);
            appState.dailyData.exercise += exercise.duration;
            
            this.reset();
            showAlert('Exercise logged successfully!', 'success');
            updateExerciseHistory();
            updateDashboard();
        });

        // Water tracking
        function addWater() {
            appState.dailyData.water++;
            updateDashboard();
            showAlert('Water glass added!', 'success');
        }

        // Weight update
        function updateWeight() {
            const weightInput = document.getElementById('weight-input');
            const newWeight = parseFloat(weightInput.value);
            
            if (!newWeight || newWeight < 50 || newWeight > 500) {
                showAlert('Please enter a valid weight between 50-500 lbs', 'error');
                return;
            }
            
            if (appState.user) {
                appState.user.weight = newWeight;
                appState.history.weights.push({
                    date: new Date().toDateString(),
                    weight: newWeight
                });
                
                weightInput.value = '';
                showAlert('Weight updated successfully!', 'success');
                updateProgress();
                updateDashboard();
            }
        }

        // Update Dashboard
        function updateDashboard() {
            if (!appState.user) return;
            
            // Update daily stats
            document.getElementById('daily-calories').textContent = appState.dailyData.calories;
            document.getElementById('calorie-goal').textContent = appState.user.calorieGoal;
            document.getElementById('daily-exercise').textContent = appState.dailyData.exercise;
            document.getElementById('daily-water').textContent = appState.dailyData.water;
            document.getElementById('current-weight').textContent = appState.user.weight + ' lbs';
            document.getElementById('target-weight').textContent = appState.user.targetWeight || 'N/A';
            
            // Update progress bars
            const calorieProgress = Math.min((appState.dailyData.calories / appState.user.calorieGoal) * 100, 100);
            const exerciseProgress = Math.min((appState.dailyData.exercise / 30) * 100, 100);
            const waterProgress = Math.min((appState.dailyData.water / 8) * 100, 100);
            
            document.getElementById('calorie-progress').style.width = calorieProgress + '%';
            document.getElementById('exercise-progress').style.width = exerciseProgress + '%';
            document.getElementById('water-progress').style.width = waterProgress + '%';
            
            // Update meal and exercise lists
            updateDailyMeals();
            updateDailyExercises();
        }

        // Update daily meals display
        function updateDailyMeals() {
            const container = document.getElementById('daily-meals');
            const todayMeals = appState.dailyData.meals;
            
            if (todayMeals.length === 0) {
                container.innerHTML = '<p class="text-gray-500 dark:text-gray-400">No meals logged yet today</p>';
                return;
            }
            
            container.innerHTML = todayMeals.map(meal => `
                <div class="flex justify-between items-center p-3 bg-gray-50 dark:bg-gray-700 rounded-lg">
                    <div>
                        <p class="font-medium">${meal.food}</p>
                        <p class="text-sm text-gray-600 dark:text-gray-400">${meal.type} • ${meal.time}</p>
                    </div>
                    <span class="font-medium text-primary">${meal.calories} cal</span>
                </div>
            `).join('');
        }

        // Update daily exercises display
        function updateDailyExercises() {
            const container = document.getElementById('daily-exercises');
            const todayExercises = appState.dailyData.exercises;
            
            if (todayExercises.length === 0) {
                container.innerHTML = '<p class="text-gray-500 dark:text-gray-400">No exercises logged yet today</p>';
                return;
            }
            
            container.innerHTML = todayExercises.map(exercise => `
                <div class="flex justify-between items-center p-3 bg-gray-50 dark:bg-gray-700 rounded-lg">
                    <div>
                        <p class="font-medium">${exercise.name}</p>
                        <p class="text-sm text-gray-600 dark:text-gray-400">${exercise.type} • ${exercise.time}</p>
                    </div>
                    <span class="font-medium text-green-500">${exercise.duration} min</span>
                </div>
            `).join('');
        }

        // Update meal history
        function updateMealHistory() {
            const container = document.getElementById('meal-history');
            const recentMeals = appState.history.meals.slice(-10).reverse();
            
            if (recentMeals.length === 0) {
                container.innerHTML = '<p class="text-gray-500 dark:text-gray-400">No meals logged yet</p>';
                return;
            }
            
            container.innerHTML = recentMeals.map(meal => `
                <div class="flex justify-between items-center p-4 bg-gray-50 dark:bg-gray-700 rounded-lg">
                    <div>
                        <p class="font-medium">${meal.food}</p>
                        <p class="text-sm text-gray-600 dark:text-gray-400">${meal.type} • ${meal.date} ${meal.time}</p>
                        <div class="text-xs text-gray-500 dark:text-gray-400 mt-1">
                            ${meal.protein > 0 ? `Protein: ${meal.protein}g` : ''} 
                            ${meal.carbs > 0 ? `Carbs: ${meal.carbs}g` : ''}
                        </div>
                    </div>
                    <span class="font-medium text-primary">${meal.calories} cal</span>
                </div>
            `).join('');
        }

        // Update exercise history
        function updateExerciseHistory() {
            const container = document.getElementById('exercise-history');
            const recentExercises = appState.history.exercises.slice(-10).reverse();
            
            if (recentExercises.length === 0) {
                container.innerHTML = '<p class="text-gray-500 dark:text-gray-400">No exercises logged yet</p>';
                return;
            }
            
            container.innerHTML = recentExercises.map(exercise => `
                <div class="flex justify-between items-center p-4 bg-gray-50 dark:bg-gray-700 rounded-lg">
                    <div>
                        <p class="font-medium">${exercise.name}</p>
                        <p class="text-sm text-gray-600 dark:text-gray-400">${exercise.type} • ${exercise.intensity} intensity</p>
                        <p class="text-xs text-gray-500 dark:text-gray-400">${exercise.date} ${exercise.time}</p>
                    </div>
                    <div class="text-right">
                        <p class="font-medium text-green-500">${exercise.duration} min</p>
                        ${exercise.calories > 0 ? `<p class="text-xs text-gray-500 dark:text-gray-400">${exercise.calories} cal</p>` : ''}
                    </div>
                </div>
            `).join('');
        }

        // Update progress view
        function updateProgress() {
            if (!appState.user) return;
            
            const currentWeight = appState.user.weight;
            const startingWeight = appState.user.startingWeight;
            const targetWeight = appState.user.targetWeight;
            
            document.getElementById('weight-input').placeholder = currentWeight;
            document.getElementById('starting-weight').textContent = startingWeight + ' lbs';
            document.getElementById('progress-current-weight').textContent = currentWeight + ' lbs';
            
            const weightChange = currentWeight - startingWeight;
            const weightChangeEl = document.getElementById('weight-change');
            weightChangeEl.textContent = (weightChange >= 0 ? '+' : '') + weightChange.toFixed(1) + ' lbs';
            weightChangeEl.className = 'font-medium ' + (weightChange < 0 ? 'text-green-500' : weightChange > 0 ? 'text-red-500' : 'text-gray-500');
            
            // Goal progress
            if (targetWeight) {
                const totalGoal = Math.abs(targetWeight - startingWeight);
                const achieved = Math.abs(startingWeight - currentWeight);
                const progress = Math.min((achieved / totalGoal) * 100, 100);
                document.getElementById('goal-progress').textContent = progress.toFixed(1) + '%';
            } else {
                document.getElementById('goal-progress').textContent = 'No target set';
            }
            
            // Weekly stats (simplified)
            const avgCalories = appState.dailyData.calories || 0;
            const totalExercise = appState.dailyData.exercise || 0;
            const activeDays = (appState.dailyData.exercise > 0 || appState.dailyData.meals.length > 0) ? 1 : 0;
            
            document.getElementById('avg-calories').textContent = avgCalories;
            document.getElementById('total-exercise').textContent = totalExercise + ' min';
            document.getElementById('active-days').textContent = activeDays + '/7';
        }

        // Profile form update
        document.getElementById('profile-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!appState.user) return;
            
            appState.user.name = document.getElementById('profile-name').value;
            appState.user.age = parseInt(document.getElementById('profile-age').value);
            appState.user.height = parseInt(document.getElementById('profile-height').value);
            appState.user.activity = document.getElementById('profile-activity').value;
            appState.user.goal = document.getElementById('profile-goal').value;
            appState.user.targetWeight = parseFloat(document.getElementById('profile-target-weight').value);
            
            // Recalculate calorie goal
            const bmr = calculateBMR(appState.user.weight, appState.user.height, appState.user.age);
            appState.user.calorieGoal = calculateDailyCalories(bmr, appState.user.activity, appState.user.goal);
            
            showAlert('Profile updated successfully!', 'success');
            updateDashboard();
        });

        // Load profile data into form
        function loadProfileForm() {
            if (!appState.user) return;
            
            document.getElementById('profile-name').value = appState.user.name || '';
            document.getElementById('profile-age').value = appState.user.age || '';
            document.getElementById('profile-height').value = appState.user.height || '';
            document.getElementById('profile-activity').value = appState.user.activity || '';
            document.getElementById('profile-goal').value = appState.user.goal || '';
            document.getElementById('profile-target-weight').value = appState.user.targetWeight || '';
        }

        // Initial load
        document.addEventListener('DOMContentLoaded', function() {
            // Check if user exists (in a real app, this would be from storage)
            if (!appState.user) {
                showView('welcome');
            } else {
                showView('dashboard');
            }
            
            // Update meal and exercise history
            updateMealHistory();
            updateExerciseHistory();
        });

        // Navigation click handler for profile
        document.querySelector('[onclick="showView(\'profile\')"]').addEventListener('click', loadProfileForm);
    </script>
</body>
</html>
