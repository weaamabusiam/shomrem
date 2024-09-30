const port = 4325;

const express = require('express');
const app = express();
app.use(express.json());

const bodyParser = require('body-parser');
app.use(bodyParser.urlencoded({extended: false}));

const path = require('path');
app.use(express.static(path.join(__dirname, "public")));

// רשימת נקודות שמירה
let points = [
    { pointName: "חדר מצלמות", location: "צפון" },
    { pointName: "מחסן ראשי", location: "מערב" },
    { pointName: "חדר שמירה", location: "דרום" },
    { pointName: "בניין משרדים", location: "מזרח" },
    { pointName: "שער ראשי", location: "מזרח" },  // נקודה חדשה
    { pointName: "חניון אורחים", location: "מערב" }  // נקודה חדשה
];


app.post('/points', (req, res) => {
    let newPoint = {
        pointName: req.body.pointName,
        location: req.body.location
    };
    points.push(newPoint);
    res.status(200).json("נקודת השמירה נוספה בהצלחה");
});


app.patch('/points/:idx', (req, res) => {
    let idx = req.params.idx;
    let updatedPoint = {
        pointName: req.body.pointName,
        location: req.body.location
    };
    points[idx] = updatedPoint;
    res.status(200).json("נקודת השמירה נערכה בהצלחה");
});


app.delete('/points', (req, res) => {
    let idx = req.query.id;
    points.splice(idx, 1);
    res.status(200).json(points);
});


app.get('/points', (req, res) => {
    res.status(200).json(points);
});


let visits = [];


app.post('/visit', (req, res) => {
    let newVisit = {
        pointName: req.body.pointName,
        visitTime: new Date()
    };
    visits.push(newVisit);
    res.status(200).json("הביקור נשמר בהצלחה");
});


app.get('/visits', (req, res) => {
    res.status(200).json(visits);
});

app.listen(port, () => {
    console.log(`Now listening on port http://localhost:${port}`);
});

