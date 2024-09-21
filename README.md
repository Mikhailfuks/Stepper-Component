<!DOCTYPE html>
<html>
<head>
  <title>Stepper Component</title>
  <style>
    .stepper {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 400px;
    }

    .step {
      width: 30px;
      height: 30px;
      border: 1px solid #ccc;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      font-weight: bold;
    }

    .step.active {
      background-color: #4caf50;
      color: white;
    }

    .step.completed {
      background-color: #8bc34a;
      color: white;
    }

    .step.disabled {
      background-color: #ccc;
      color: #888;
    }

    .connector {
      width: 70px;
      height: 1px;
      background-color: #ccc;
    }

    .connector.active {
      background-color: #4caf50;
    }

    .connector.completed {
      background-color: #8bc34a;
    }
  </style>
</head>
<body>
  <div class="stepper">
    <div class="step active">1</div>
    <div class="connector active"></div>
    <div class="step completed">2</div>
    <div class="connector completed"></div>
    <div class="step disabled">3</div>
  </div>

  <script>
    const steps = document.querySelectorAll('.step');

    // Update the active and completed steps based on the current step
    function updateSteps(currentStepIndex) {
      for (let i = 0; i < steps.length; i++) {
        const step = steps[i];

        if (i < currentStepIndex) {
          step.classList.add('completed');
          step.classList.remove('active');
        } else if (i === currentStepIndex) {
          step.classList.add('active');
          step.classList.remove('completed');
        } else {
          step.classList.remove('active');
          step.classList.remove('completed');
          step.classList.add('disabled');
        }
      }

      // Update connectors
      const connectors = document.querySelectorAll('.connector');
      for (let i = 0; i < connectors.length; i++) {
        const connector = connectors[i];

        if (i < currentStepIndex) {
          connector.classList.add('completed');
          connector.classList.remove('active');
        } else {
          connector.classList.remove('completed');
          connector.classList.add('active');
        }
      }
    }

    // Click event listener for steps
    steps.forEach((step, index) => {
      step.addEventListener('click', () => {
        updateSteps(index);
      });
    });
  </script>
</body>
</html>
