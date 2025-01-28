
const express = require("express");
const bodyParser = require("body-parser");
const app = express();
const PORT = 5000;

app.use(bodyParser.json());

// Simulated database
let users = [
  { id: 1, name: "John Doe", isPremium: false },
];

app.post("/api/upgrade", (req, res) => {
  const { userId } = req.body;
  const user = users.find((u) => u.id === userId);
  if (user) {
    user.isPremium = true;
    res.status(200).send({ message: "Upgrade successful." });
  } else {
    res.status(404).send({ message: "User not found." });
  }
});

app.listen(PORT, () => {
  console.log(`Server is running on http://localhost:${PORT}`);
});
