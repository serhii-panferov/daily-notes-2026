## 2025-12-09

### ⭐ What I learned
- Refresh knowledge about ssh encode
- PHP Fibers
```
class Scheduler {
    private array $tasks = [];

    public function add(Fiber $fiber) {
        $this->tasks[] = $fiber;
    }

    public function run() {
        while ($this->tasks) {
            $fiber = array_shift($this->tasks);

            if (!$fiber->isStarted()) {
                $fiber->start();
            } else {
                $fiber->resume();
            }

            if ($fiber->isSuspended()) {
                $this->tasks[] = $fiber;
            }
        }
    }
}
$scheduler = new Scheduler();
$scheduler->add(new Fiber(function () {
    for ($i = 1; $i <= 3; $i++) {
        echo "Task A: $i\n";
        Fiber::suspend();
    }
}));
$scheduler->add(new Fiber(function () {
    for ($i = 1; $i <= 2; $i++) {
        echo "Task B: $i\n";
        Fiber::suspend();
    }
}));
$scheduler->run();
```

### 🛠 What I built or improved
- Preparing to integration with Google Actions Center
- Refactoring legacy functionality
- Improved CI actions to prevent workflow failures.

### 🔍 Notes / Discoveries
- Progress doesn't happen on its own - you need to push it forward.

### 🎯 Next small step
- Compare fibers wih Goroutine, learn HTTP example, await/async on PHP etc.
